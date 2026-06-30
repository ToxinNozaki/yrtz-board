# yrtz board

private idea board for the group. password protected. if you don't have the password you're not supposed to be here.

---

drop ideas as notes. react to them, vote in or nah, and open a thread on any post to hash it out in realtime — like a discord thread but scoped to the idea.

---

## stack

- **github pages** — static hosting, no server
- **supabase** — postgres database, realtime subscriptions, image storage
- **vanilla js** — no framework, no bundler, one html file

---

## features

- password gate (sha-256 hashed, plaintext never in source)
- post ideas with a title, description, and up to 3 images
- reactions: fire, love, eyes, in, nah — toggleable, live for everyone
- per-note discussion threads with realtime chat
- sort by newest, most hyped, or most wanted
- edit your own posts (tracked by browser fingerprint, no account needed)
- admin mode for the owner — full edit/delete on any post, auto-detected by ip
- 60 second cooldown between posts per device
- images stored in supabase storage, persist with the note
- new posts and reactions appear live without refreshing

---

## local dev

open `index.html` in a browser. no build step, no dependencies to install.

---

## notes

the admin ip check runs silently on login. if your ip matches, admin controls appear on cards without any setup. if your ip changes (different network, vpn), click the small `mod` text in the bottom-right corner to re-check.

image uploads go directly from the browser to supabase storage. nothing touches a server.

the browser fingerprint is a sha-256 hash of your user agent, screen size, timezone, and hardware info. it's consistent across sessions on the same device. if you clear localStorage the fingerprint regenerates and you lose edit access to old posts.
