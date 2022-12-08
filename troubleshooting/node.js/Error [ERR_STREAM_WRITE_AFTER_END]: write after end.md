Error [ERR_STREAM_WRITE_AFTER_END]: write after end
---
node.js 서버 구축하는데 제목과 같은 에러를 만남..
검색 결과 end가 두 번 있어서 그렇다는데...

문제의 코드
---
```
 let body = [];

 if (request.method === 'OPTIONS') {
  response.writeHead(200, defaultCorsHeader);
  response.end();
}

if (request.method === 'POST') {
  request
    .on('data', (chunk) => {
      body.push(chunk);
    })
    .on('end', () => {
      body = Buffer.concat(body).toString();
      response.writeHead(201, defaultCorsHeader);
      if (request.url === '/upper') {
        response.end(body.toUpperCase());
      } else if (request.url === '/lower') {
        response.end(body.toLowerCase());
      }
    });
} else {
  response.writeHead(404, defaultCorsHeader);
  response.end('bad');
}
//이렇게 짜면 문제가 되는 이유는 옵션스가 메소드일때 13번째 줄에 엔드가 실행되고 
// else를 타고 32번째 줄에 엔드도 실행이됨...
//단순히 체이닝 되어 있지 않아서 괜찮을거라고 생각했는데 
//응... 아니야...그래서 아래와 같이 else if로 코드를 체이닝 해줌...
```

똑바로 짠 코드
---
```
const http = require('http');

const PORT = 4999;

const ip = 'localhost';

const server = http.createServer((request, response) => {
 //const { headers, method, url } = request;
 let body = [];

 if (request.method === 'OPTIONS') {
  response.writeHead(200, defaultCorsHeader);
  response.end();
}else if (request.method === 'POST') {
  request
    .on('data', (chunk) => {
      body.push(chunk);
    })
    .on('end', () => {
      body = Buffer.concat(body).toString();
      response.writeHead(201, defaultCorsHeader);
      if (request.url === '/upper') {
        response.end(body.toUpperCase());
      } else if (request.url === '/lower') {
        response.end(body.toLowerCase());
      }
    });
} else {
  response.writeHead(404, defaultCorsHeader);
  response.end('bad');
}

});

server.listen(PORT, ip, () => {
  console.log(`http server listen on ${ip}:${PORT}`);
});

const defaultCorsHeader = {
  'Access-Control-Allow-Origin': '*',
  'Access-Control-Allow-Methods': 'GET, POST, PUT, DELETE, OPTIONS',
  'Access-Control-Allow-Headers': 'Content-Type, Accept',
  'Access-Control-Max-Age': 10
};
```
