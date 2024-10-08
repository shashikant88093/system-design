# Key Terms

> IP
  Stands for  Internet Protocol. This network protocol outlines how almost all machine-to-machine communications should happen
  in the world. Other protocols like TCP,UDP and HTTP are built on top of IP

> TCP
  Stands for Transmission Control Protocol. This protocol is used to ensure that data packets are delivered in the
  correct order and that the data is not corrupted during transmission.

  Network protocol built on top of the Internet Protocol(IP). Allows for ordered, reliable data delivery between machines over the public internet by creating a **connection**.

  TCP is usually implemented in the kernel, which exposes **sockets** to applications that they can use to stream data through an open connection

> HTTP
  The HyperText Transfer Protocol is very common network protocol implemented on top of TCP. CLients make HTTP requests, and servers respond with a response.

  Request typically have the following schema:

  ```
  host : string (example: algoexport.io)
  port : integer (example : 80 or 443)
  method : string (example: GET,PUT,POST,DELETE,OPTIONS or PATCH)
  header: pair list (example: "Content-Type" => "application/json")
  body: opaque sequence of bytes
  ```
  Response typically have the following schema:

  ```
  status_code : integer (example: 200,404,500)
  header: pair list (example: "Content-Type" => 1238)
  body: opaque sequence of bytes
  ```

> IP Packet
  
  Sometimes more broadly referred to as just a (network) **packet**, an IP packet is effectively the smallest unit used to describe
  data being sent over IP , aside from bytes. An IP packets consist of:

  ** an **IP header**, which contains the source and destination ""IP addresses** as well as other information related to the network
  ** a **payload**, which is the actual data being sent over the network.
