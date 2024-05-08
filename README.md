## Tutorial 10 - Broadcast Chat

Nama: Sita Amira Syarifah

NPM: 2206023023

Kelas: C


To run the program with the specification of 1 server and 3 clients, I executed the command `cargo run --bin server` in one terminal and ran the command `cargo run --bin client` in three other terminals in IntelliJ. When I send a message (type text) from client 1, the server receives the message and broadcasts it to all clients (clients 2, 3, including client 1 that sent the text). Similarly, when I send/type text from client 2, it will be broadcasted by the server to other clients.