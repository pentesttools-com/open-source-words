wrk a http benchmarking tool wrk is a modern http benchmarking tool capable of generating significant load when run on a single multi core cpu it combines a multithreaded design with scalable event notification systems such as epoll and kqueue an optional luajit script can perform http request generation response processing and custom reporting details are available in scripting and several examples are located in scripts basic usage wrk t12 c400 d30s http 127 0 0 1 8080 index html this runs a benchmark for 30 seconds using 12 threads and keeping 400 http connections open output running 30s test http 127 0 0 1 8080 index html 12 threads and 400 connections thread stats avg stdev max stdev latency 635 91us 0 89ms 12 92ms 93 69 req sec 56 20k 8 07k 62 00k 86 54 22464657 requests in 30 00s 17 76gb read requests sec 748868 53 transfer sec 606 33mb command line options c connections total number of http connections to keep open with each thread handling n connections threads d duration duration of the test e g 2s 2m 2h t threads total number of threads to use s script luajit script see scripting h header http header to add to request e g user agent wrk latency print detailed latency statistics timeout record a timeout if a response is not received within this amount of time benchmarking tips the machine running wrk must have a sufficient number of ephemeral ports available and closed sockets should be recycled quickly to handle the initial connection burst the servers listen 2 backlog should be greater than the number of concurrent connections being tested a user script that only changes the http method path adds headers or a body will have no performance impact per request actions particularly building a new http request and use of response will necessarily reduce the amount of load that can be generated acknowledgements wrk contains code from a number of open source projects including the ae event loop from redis the nginx joyent node js http parser and mike palls luajit please consult the notice file for licensing details cryptography notice this distribution includes cryptographic software the country in which you currently reside may have restrictions on the import possession use and or re export to another country of encryption software before using any encryption software please check your countrys laws regulations and policies concerning the import possession or use and re export of encryption software to see if this is permitted see http www wassenaar org for more information the u s government department of commerce bureau of industry and security bis has classified this software as export commodity control number eccn 5d002 c 1 which includes information security software using or performing cryptographic functions with symmetric algorithms the form and manner of this distribution makes it eligible for export under the license exception enc technology software unrestricted tsu exception see the bis export administration regulations section 740 13 for both object code and source code