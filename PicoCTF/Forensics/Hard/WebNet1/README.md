
## How to solve

Desc: We found this packet capture and key. Recover the flag.

Hint 1: Try using a tool like Wireshark.

Hint 2: How can you decrypt the TLS stream?

1. Open the packet capture using wireshark

2. ![alt text](image.png)

3. Dapat kita lihat bahwa terdapat 2 protocol yaitu TCP dan TLS

4. Jika kita lihat di hint 2 kita diminta untuk mengetahui bagaimana ngedecrypt protocol TLS stream

5. Kalo kita lihat dari definisi, A TLS stream refers to a secure data stream that uses TLS (Transport Layer Security) to encrypt the communication between two endpoints—typically between a client and a server.

6. ![alt text](image-1.png)

7. Jadi simpelnya TLS Protocol stream adalah stream yang dienkripsi

8. Kalo dilihat dari file yang diberikan challenge, sepertinya key-nya itu key enkripsi dari TLS Stream

9. Kita bisa dengan mudah cari gimana ngedecrypt TLS Stream pake key

10. https://blog.didierstevens.com/2020/12/14/decrypting-tls-streams-with-wireshark-part-1/

11. Kita bisa memasukan key yang dikasih di Edit > Preferences > Protocols > TLS > Edit > RSA Key List

12. Setelah kita masukan keynya, new stream with HTTP protocol muncul

13. ![alt text](image-2.png)

14. Kalo kita bandingkan dengan WebNet0, pada WebNet1 ini ada tambahan jenis file selain html dan css yaitu image .jpeg dan .ico

15. Jika kita follow stream HTTP maka kita akan lihat flagsnya, namun flags ini flag palsu

16. ![alt text](image-3.png)

17. Kita bisa coba mengexport HTTP object tadi seperti html, css, jpeg, dan ico

18. ![alt text](image-4.png)

19. Setelah kita buka second html maka tampilannya akan seperti ini

20. ![alt text](image-5.png)

21. Setelah diinspect sepertinya tidak ada apa apa

22. ![alt text](image-6.png)

23. Jika kita coba lihat metadata vulture.jpg menggunakan exiftool maka kita bisa melihat flags aslinya

24. ![alt text](image-7.png)
