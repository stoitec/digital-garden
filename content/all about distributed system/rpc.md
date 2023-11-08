---
title: RPC - Remote Procedure Call
tags:
  - programming
draft: false
---
Remote Procedure Call, or RPC, is a fundamental concept in [[distributed system]] where a function call appears to be local but is actually executed on a different node.
## How it works ?
![[src/img/Pasted image 20231107221325.png]]This process is facilitated by a stub function, which acts as a local stand-in for the remote function. When a call is made, the arguments are marshalled, meaning they are encoded into a format suitable for network transmission, such as JSON or a binary format. Once the message reaches its destination, it is unmarshalled, then converted back the message by the RPC Server into the data types that the programming language of the recipient's node can understand and use. 
This mechanism allows systems to communicate across different environments seamlessly, as if they were part of a single, unified system.
![[src/img/Pasted image 20231107222439.png]]
## Interoperability and IDL
RPC uses IDL to facilitate interoperability between services written in different languages, an example of IDL is gRPC, with gRPC we have .proto files which facilitate the setup of structures of requests and responses, along with the specification of available RPC's function and their input/output messages.

```proto
message PaymentRequest {
	message Card {
		required string cardNumber = 1;
		optional int32 expiryMonth = 2;
		optional int32 expiryYear = 3;
		optional int32 CVC = 4;
	}
	
	enum Currency { GBP = 1; USD = 2; }
	
	required Card card = 1;
	required int64 amount = 2;
	required Currency currency = 3;
}

message PaymentStatus {
	required bool success = 1;
	optional string errorMessage = 2;
}

service PaymentService {
	rpc ProcessPayment(PaymentRequest) returns (PaymentStatus) {}
}
```

**Links:**
- [[distributed system]]