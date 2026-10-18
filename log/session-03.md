# Session 3 (started 2026-10-18)
- Hours: 

## Bandit 11 -> 12
Goal: decode text in data.txt that was rotated by 13 positions (ROT13) to get the password.
What I didn't know: what "rotated" meant (a Caesar cipher: each letter shifts N places, only letters change, upper and lower case rotate separately). I also didn't know which command to use.
First attempt: `cat data.txt | tr 'a-z' 'nopqrstuvwxyzabcdefghijklm'`. It decoded only lowercase. The output began "Ghe" instead of "The", so uppercase letters stayed scrambled and the password was wrong.
Stuck: first on finding the right command (tr), then on its flags (the mapping has to cover both cases).
Hints used: yes, I asked what "rotated" meant, and got a hint to cover uppercase as well.
Final command that worked: cat data.txt | tr 'a-zA-Z' 'nopqrstuvwxyzabcdefghijklmNOPQRSTUVWXYZABCDEFGHIJKLM' 

## Bandit 12 -> 13
Goal: the password is in a hexdump of a file that was compressed many times.
Commands: `xxd -r` (hexdump back to binary), `file`, `mv`, then the matching decompression tool each round.
What I didn't know: that `strings` is useless here (only gibberish), that `file` identifies by content, and that I can't write in my home dir, so I worked in a folder under /tmp.
Stuck: `gzip -d` failed even after I renamed the file. What fixed it: rename the file extension to the proper suffix ;
Method I worked out: run `file`, get the right suffix, rename, decompress with the matching tool, repeat until it's plain ASCII text. It took a lot of rounds.
Hints used: yes, 3 hints (use `file`, the BZh header, rename for the suffix).
