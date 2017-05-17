本项目是基于发布订阅者模式实现的消息通信框架

主要实现的功能有：订阅消息，发布消息，解除消息等。

基本用法举例：
$("#elem").click(function(event) {
    //发布key值为test的消息，并传入一个用数组封装的参数1和2，
    PubSubEvent.publish("test",[1,2]);
    //根据返回值取消订阅
    PubSubEvent.unsubscribe(testToken);
    //根据key值取消订阅
    PubSubEvent.unsubscribe("test");
    //也可以传入订阅函数名取消订阅
    PubSubEvent.unsubscribe(funA);
});
var funA = function(a,b){
    alert("funA"+a+b);
}
//“test”为订阅的key，funA是回调函数，可以传入一个定义好的函数，并返回一个订阅的token
var testToken = PubSubEvent.subscribe("test",funA);
//回调函数也可以是一个匿名函数
var token = PubSubEvent.subscribe("test",function(a,b){
    alert("anomouse"+a+b);
});
