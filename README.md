# MERN-recap

## Rest and WebApi
Rest - Restfull state transfer - It is a architectural style<br/>
Communication uses GET,POST,PUT,DELETE<br/>
supports json xml<br/>
WebApi-Boarder term accessed over the web<br/>
SOAP - Simple object access api - for secure , and for using multiple languages , it uses xml<br/>

## HTTP1 and HTTP2

http1.1 - loading , single connection  ,single request at a time, take time <br/>
http2 - compress http headers , allows server push , enaples muliplexing<br/>
uses HPACK wich compress <br/>
additional info : http/0.9 only get get request ,<br/>
/0.1 - get post ,head methods , content type , content length <br/>
/1.1 - pipelining ,better caching mechanism , put, delete , options <br/>
/2 - multiplexing , binary farming ,hpack(reduce size),connection priorization <br/>
/3 tcp to quic , reduce latency and quick performance <br/>

