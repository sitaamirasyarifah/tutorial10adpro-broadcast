## Tutorial 10 - Broadcast Chat

Nama: Sita Amira Syarifah

NPM: 2206023023

Kelas: C

### 2.1. Original Code of Broadcast Chat
![WhatsApp Image 2024-05-08 at 16 15 52](https://github.com/sitaamirasyarifah/tutorial10adpro-broadcast/assets/122429830/d1068301-d033-44a5-9ebf-b9fba587edab)

To run the program with the specification of 1 server and 3 clients, I executed the command `cargo run --bin server` in one terminal and ran the command `cargo run --bin client` in three other terminals in IntelliJ. When I send a message (type text) from client 1, the server receives the message and broadcasts it to all clients (clients 2, 3, including client 1 that sent the text). Similarly, when I send/type text from client 2, it will be broadcasted by the server to other clients.

### 2.2. Modifying the websocket port
![WhatsApp Image 2024-05-08 at 16 18 01](https://github.com/sitaamirasyarifah/tutorial10adpro-broadcast/assets/122429830/3eded1ee-76ae-4727-a31a-1f092a7d5cd1)

![WhatsApp Image 2024-05-08 at 16 23 21](https://github.com/sitaamirasyarifah/tutorial10adpro-broadcast/assets/122429830/ee5d0368-e50d-478e-8f01-90ecac21a2ef)

When port 8080 is only changed on one side (for example, on the client side), an error will occur on the client because the client's port is not connected to the server. The server only provides port 2000.

To prevent errors, modifications are needed to change the port to 8080 in both files, namely the client file and the server file. In the `client.rs` file, the default port in the Uri of the `ClientBuilder` that builds the WebSocket connection on the client needs to be changed. Meanwhile, in the server file, port 8080 should be replaced in its `listener` variable, which serves as the TCP listener for the connection, and in the print query that indicates that the server is listening on port 8080. When the port is the same in both files, the program will run as expected, just like when using port 2000.

### 2.3. Small changes. Add some information to client
![WhatsApp Image 2024-05-08 at 16 24 39](https://github.com/sitaamirasyarifah/tutorial10adpro-broadcast/assets/122429830/338dfe17-3da0-4686-a378-b52a37025d63)

To include information about the sender's IP address and port on each client, you have modified the text format broadcasted in the `server.rs` file. Initially, the broadcasted text used `bcast_tx.send(text.into())?;`, but you modified it to include the sender's IP address using the new format `bcast_tx.send(format!("{addr} : {text}"))?;`. This way, each broadcasted message will include information about the sender's IP address along with the text of the message itself.
