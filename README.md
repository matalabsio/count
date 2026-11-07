# PPM Counting Day: deployment notes

Static site. No build step, no backend, no environment variables.

Files
- index.html : the whole page (photos and fonts config included)
- snap.json  : the numbers the page shows. It fetches this every 30 seconds.
- vercel.json: stops snap.json being cached

Deploy (Vercel)
1. Put these 3 files at the root of a new GitHub repo.
2. Vercel > Add New > Project > import the repo. Framework preset: Other. Leave build command and output directory empty.
3. Deploy and open the URL. It should say "No results have been published yet."
4. Optional custom domain, e.g. count.matalabs.io: Project > Settings > Domains > add it, then add the DNS record Vercel shows (usually a CNAME to cname.vercel-dns.com).

Updating the numbers (repeat through the day)
1. The owner sends you a block of JSON ("snapshot").
2. Replace the ENTIRE contents of snap.json with it and commit to main.
3. Vercel redeploys (under a minute). Open pages refresh by themselves.
If the JSON is malformed the page keeps the previous numbers.

Test before sharing the link
- Paste a snapshot, wait for the deploy, confirm the numbers appear on a second phone.
- Check the page loads on a phone and the tabs scroll sideways.
- The only external link on the page is "Built by MATA Labs" to matalabs.io.
