# Session 4 (started 2026-10-22)
- Hours: 1h 

## Bandit 16 -> 17
Goal: submit the current password to the one server on localhost between ports 31000 and 32000 that speaks SSL, to get the next credential.
Commands: `nmap -p31000-32000 localhost` (plain `nmap localhost` did not show them; I found `-p` in `man nmap`), then `openssl s_client -connect localhost:<port>` on each open port. Wrong servers echo back whatever I send.
Stuck: 21 min. After the right server accepted the password, s_client kept asking for a KEYUPDATE instead of showing the reply. I asked ChatGPT and it suggested adding `-tls1_3 -adv`; that fixed it. I don't yet know why. I did not need the {key:noreq} command that -adv allows.
To check: read `man s_client`, section CONNECTED COMMANDS, to understand what triggered this.
Hints used: yes, asked ChatGPT about the KEYUPDATE problem.


## Bandit 17 -> 18
Goal: find the one line that differs between two password files.
Commands: `diff passwords.old passwords.new`
Time: about 1 min. Stuck: no. Hints used: none.

## Bandit 18 -> 19
Goal: read the `readme` file, but logging in kicks me out because .bashrc was modified to log me out.
Commands: `ssh bandit18@bandit.labs.overthewire.org -p 2220 "cat readme"`
What I learned: ssh can run a single command on the server and print the output without opening an interactive shell, which gets around the .bashrc kick-out.
Time: 4:30. Stuck: logging in. Hints used: asked ChatGPT whether ssh can run commands without connecting, and it gave me the syntax.

## Bandit 18 -> 19
Goal: read the `readme` file, but logging in kicks me out because .bashrc was modified to log me out.
Commands: `ssh bandit18@bandit.labs.overthewire.org -p 2220 "cat readme"`
What I learned: ssh can run a single command on the server and print the output without opening an interactive shell, which gets around the .bashrc kick-out.
Time: 4:30. Stuck: logging in. Hints used: asked ChatGPT whether ssh can run commands without connecting, and it gave me the syntax.

## Bandit 19 -> 20
Goal: use the setuid binary `bandit20-do` to read /etc/bandit_pass/bandit20.
Commands: `ls -la` (saw I only have read and execute on the binary, no write), then `./bandit20-do cat /etc/bandit_pass/bandit20`
What I tried first: editing the binary or writing a script, which failed because I can't write to it.
What I learned: a setuid program runs with its owner's privileges, so any command it launches (here `cat`) also reads files as the owner.
Time: 9 min. Hints used: none.

## Bandit 19 -> 20
Goal: use the setuid binary `bandit20-do` to read /etc/bandit_pass/bandit20.
Commands: `ls -la` (saw I only have read and execute on the binary, no write), then `./bandit20-do cat /etc/bandit_pass/bandit20`
What I tried first: editing the binary or writing a script, which failed because I can't write to it.
What I learned: a setuid program runs with its owner's privileges, so any command it launches (here `cat`) also reads files as the owner.
Time: 9 min. Hints used: none.

## Bandit 20 -> 21
Goal: use the setuid binary `suconnect <port>`, which connects to a port, reads what it receives, compares it with bandit20's password, and sends the next password back if they match.
Commands: two tmux panes. Pane 1: `nc -lv 1234` (listener). Pane 2: `./suconnect 1234`. I typed bandit20's password into the listener and got the next password back.
What I didn't know: how to run two sessions at once (learned tmux), and how to open a port myself (found `nc -lv <port>`).
Time: 20 min 30 s. Hints used: none.
