# MERN-recap

## Rest and WebApi
Rest - Restfull state transfer - It is a architectural style
Communication uses GET,POST,PUT,DELETE
supports json xml
WebApi-Boarder term accessed over the web
SOAP - Simple object access api - for secure , and for using multiple languages , it uses xml

## HTTP1 and HTTP2

http1.1 - loading , single connection  ,single request at a time, take time 
http2 - compress http headers , allows server push , enaples muliplexing
uses HPACK wich compress 
additional info : http/0.9 only get get request ,
/0.1 - get post ,head methods , content type , content length 
/1.1 - pipelining ,better caching mechanism , put, delete , options 
/2 - multiplexing , binary farming ,hpack(reduce size),connection priorization 
/3 tcp to quic , reduce latency and quick performance 

