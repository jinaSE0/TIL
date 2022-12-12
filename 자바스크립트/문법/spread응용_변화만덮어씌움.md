서버만드는 중에 spread 문법 꿀팁을 알았음,,,
스프레드 문법은 **변화된 것만** 덮어씌워준다
```
update: (req, res) => {
    const { uuid } = req.params;
    const bodyData = req.body;
     // TODO:
    if(uuid){
      let changeDataIndex = flights.findIndex((el)=>el.uuid===uuid)
        
      //처음 작성한 코드 
      // uuid,
      //(요청값이 같거나 언디파인드)? 그대로 : 요청한 값
      // departure: (bodyData.departure===undefined||flights.departure===bodyData.departure)?flights[changeDataIndex].departure:bodyData.departure,
      // destination: (bodyData.destination===undefined||flights.destination===bodyData.destination)?flights[changeDataIndex].destination:bodyData.destination,
      // departure_times: (bodyData.departure_times===undefined||flights.departure_times===bodyData.departure_times)?flights[changeDataIndex].departure_times:bodyData.departure_times,
      // arrival_times:  (bodyData.departure_times===undefined||flights.arrival_times===bodyData.arrival_times)?flights[changeDataIndex].arrival_times:bodyData.arrival_times
     
       //spread응용
        flights.splice(changeDataIndex,1,{
          ...flights[changeDataIndex], //바꾸고싶은애 전체 정보
          ...bodyData //스프레드는 변화만 덮어씌워줌 
     })
      return res.status(200).json(flights[changeDataIndex])
  }

  //요청한 정보가 틀리면
  res.status(500).json({error : "정보를 입력하세요"})
}
```
