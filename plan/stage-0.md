# Stage 0: Foundations (4 weeks, 20 days, ~40h)

Daily format: 15 min recall (no notes), 75 min lab, 30 min log + commit (`log/YYYY-MM-DD.md`).
Skim anything the diagnostic shows you already know. Only test machines you own.

## Week 1: Linux and shell
- **Day 1 (Mon 12 Oct):** Take the diagnostic (`gates/stage-0-diagnostic.md`). Then OverTheWire Bandit levels 0-5.
- **Day 2:** Bandit 6-10. Linux Journey: permissions, `find`, `grep`.
- **Day 3:** Bandit 11-15 (encoding, ssh, nc).
- **Day 4:** Bandit 16-20. Read `man` pages for every command you did not know.
- **Day 5 (checkpoint):** Re-solve 3 earlier levels from scratch, timed. Write a personal command cheat sheet in the log.

## Week 2: Networking
- **Day 6:** TCP/IP model, IP addressing, subnetting practice (do 10 subnet problems by hand).
- **Day 7:** DNS and DHCP. Use `dig` and `nslookup` on real domains; explain each record type.
- **Day 8:** TCP vs UDP, handshake, ports. Capture your own traffic in Wireshark and find a handshake.
- **Day 9:** TLS/HTTPS basics. Run nmap against your own VM only and explain every line of output.
- **Day 10 (checkpoint):** Capture a login to a local site and explain each packet. Redo 5 subnet problems timed.

## Week 3: HTTP and web basics
- **Day 11:** HTTP methods, status codes, headers (MDN HTTP docs).
- **Day 12:** Cookies, sessions, same-origin policy, CORS.
- **Day 13:** Install Burp Suite Community, proxy your browser, intercept requests to a local app.
- **Day 14:** Proxy your own Next.js/Supabase app. List every request, header, and token it sends.
- **Day 15 (checkpoint):** Find 3 things in your own app's traffic worth worrying about. Write them up in notes.

## Week 4: Python and bash for security
- **Day 16:** Python refresher (Automate the Boring Stuff): files, strings, functions.
- **Day 17:** Python `requests`: script that fetches a URL and prints status and headers.
- **Day 18:** Python sockets: write a simple TCP port scanner (own machines only).
- **Day 19:** Bash loops and pipes: script that scans your own host's ports and parses a log file.
- **Day 20 (checkpoint):** Clean up both tools, put them in `projects/stage0-tools/` with a README.

## Gate week (Week 5, Mon-Tue)
Timed exam from Claude, oral defense, one published write-up in `writeups/`.
Results in `gates/stage-0-gate.md`. No Stage 1 until passed.
