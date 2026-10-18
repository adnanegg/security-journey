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

## Bandit 13 -> 14
Goal: the level gives an SSH private key instead of a password, to log in as the next user.
Commands: copied the key text, `exit`, `nano` to save it as a key file on my machine, `chmod` to remove group/others permissions: chmod 700 banditkey, then `ssh` with the key file: ssh -i ./banditkey.
What I learned: ssh key login (private key instead of a password), and ssh refuses a key that group or others can read. I only found this out when it warned me.
Stuck: nothing serious, the level was easy.
Hints used: none, I read the level's own hint.

## Bandit 13 -> 14
Goal: the level gives an SSH private key instead of a password, to log in as the next user.
Commands: copied the key text, `exit`, `nano` to save it as a key file on my machine, `chmod` to remove group/others permissions: chmod 700 banditkey, then `ssh` with the key file: ssh -i ./banditkey.
What I learned: ssh key login (private key instead of a password), and ssh refuses a key that group or others can read. I only found this out when it warned me.
Stuck: nothing serious, the level was easy.
Hints used: none, I read the level's own hint.

## Bandit 14 -> 15
Goal: submit the current level's password to port 30000 on localhost to get the next password.
First attempts: `nc localhost 30000` and typed random input, which only returned "password incorrect". I found a public key in `~/.ssh/authorized_keys` (comment rudy@localhost) and wrongly thought the SSH key I used to log in was the "current level password". ChatGPT said a public key alone can't give access, which was true but didn't solve it.
What I didn't know: an SSH key and a level password are two separate credentials, and I didn't know where the level's own password is stored. The path was in the previous level's goal text, which I'd missed.
Stuck: 20+ min on this.
Hints used: yes, I got the password file location from a hint.
Final command that worked: nc localhost 30000 

## Bandit 14 -> 15
Goal: submit the current level's password to port 30000 on localhost to get the next password.
First attempts: `nc localhost 30000` and typed random input, which only returned "password incorrect". I found a public key in `~/.ssh/authorized_keys` (comment rudy@localhost) and wrongly thought the SSH key I used to log in was the "current level password". ChatGPT said a public key alone can't give access, which was true but didn't solve it.
What I didn't know: an SSH key and a level password are two separate credentials, and I didn't know where the level's own password is stored. The path was in the previous level's goal text, which I'd missed.
Stuck: 20+ min on this.
Hints used: yes, I got the password file location from a hint.
Final command that worked: nc localhost 30000 
