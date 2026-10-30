# Red & Gold Golf

A 3D, Chaminade-themed golf game that runs in any browser. Everything is in one file, index.html, with no install and no build step.

Play it at https://chamigolf.github.io/ (or on the Netlify copy for Wi-Fi that blocks github.io and vercel.app: see "Hosting on Netlify" below).

## How to play

- Check PIN at the top for yards to the hole, then pick a club. Tap the club name to open your bag, or use the arrow buttons.
- Swipe left or right to aim. MAP shows the whole hole, and you can tap it to aim.
- Press the ball and pull back. Every shot works like putting: the tag next to the ball shows your swing % (100% = the club's full distance) with a rough distance guide underneath.
- Let go in the bright gold zone for a perfect strike.
- Putting: aim exactly with the ◀ AIM ▶ buttons in the bottom-left corner (hold to keep turning) or the left/right arrow keys (Shift = bigger steps; up/down arrows change club). Wind never moves a putt (it barely touches little chips either).
- Momentum: 3 holes in a row with no bogey adds +20% to hole payouts, then +20% more per hole you keep it going, with no limit. A bogey ends it.
- Rough cuts distance 15% and sand cuts it 40% (less with the Sand Wedge). The driver only gets its full distance off a tee: hit it off the fairway (or anywhere else) and it loses 20%. Watch the wind arrow.
- After every shot the game picks the club whose full swing finishes closest to the hole. On doglegs it only plays to the corner when trees block the line to the hole.
- Water and out of bounds cost a stroke. Cart paths are concrete: the ball kicks up and skips off them.
- Left-handed? Switch hands in the Golfer tab.
- Golf ball colours are free: pick a preset or mix any colour in Golfer > Ball with the colour mixer (big hue/shade pad, brightness, R/G/B sliders with +/- buttons and number boxes, a colour code box and quick swatches). Alignment lines still cost money. The same mixer makes custom outfit colours ($1,050 each, bought once).
- On the first tee, Mr. Haslbaur (3C Par Three) and Mr. Garner (Chami Links Crimson) pop up in the bottom-left corner with a word of encouragement (tap to dismiss; they leave after your tee shot).
- Hole payouts: hole-in-one $1,500 · albatross $1,000 · eagle $250 · birdie $100 · par $25 · bogey or worse $0.
- Driving Range (Play tab): free (Oct 28 2026), with range money capped at $1,000 a day (Eastern time). A bucket of 30 balls and eight target greens from 50 to 270 yds, each with a bucket in the middle. In the bucket pays $105 to $303 (by distance), inside the inner ring $17 to $40, on the target green $10 to $17, and every target hit in a row adds +10% (up to +50%). "Another bucket" reuses the bucket: +5% per reuse and the streak carries on, up to 10 reuses in a row; after that it's a fresh bucket again. Range money is capped at $1,000 a day. Floating money, cash-register sounds, confetti for a bucket and a summary card at the end.
- Updates: the What's New pop-up shows the update number, and "📜 Previous updates" (also under Stats) lists every update.

## Courses

3C Par Three (6 holes, where everyone starts) → Chami Links Crimson (6 holes) → Chami Links Gold (Bethpage Black's front nine, 9 holes) → Chami Links Black (all 18 holes of Bethpage Black, the hardest course), plus TPC Saragosa (9 holes), Faerber Lake, Meribah Country Club, Brothers Hollow and Deans Valley (its 18th hole is Room 23), Gold Star Mini Golf, the Driving Range and the Daily Closest to the Pin.

New on Oct 27 2026: **Founders Park** (9 holes, autumn parkland, unlocks after Chami Links Crimson), **Hearst Executive** (18 short holes, mostly par 3s, a city course at dusk, after TPC Saragosa), **Darby Beach** (9 seaside links holes, after Faerber Lake) and **Flyers Presidential** (9 long, tight championship holes, after Chami Links Gold). Each has its own leaderboard and Daily Tournament. (Faerber Lake was called Farbor Lake: its internal id is still `farbor`, so every old score and stat carried over.)

Trees: only the trunk is a hard bounce. Flying into the leaves, 30% of the time the ball catches a branch and drops; 70% of the time it carries on, but the rest of the shot only goes about half as far.

Daily Closest to the Pin: 14 layouts (island, long and tight, bunker gauntlet, cliff edge, wedge wizard, postage stamp, redan, big drop, uphill fortress, forest chute, peninsula, desert waste, punchbowl, double water), never the same layout two days running, a new pin spot every day, calm to gusty wind, and uphill/downhill tees (1 yd of elevation = 1 yd of carry, shown as "plays like").

Gold Star Mini Golf was reworked on Oct 20 2026 (par 41: 13 par 2s and 5 par 3s). Golfers were birdieing the old par 3s, so every hole was balanced with a computer golfer that takes thousands of simulated putts per hole: a good player now averages about 2.1 to 2.4 on the par 2s and 2.6 to 3.1 on the par 3s (Zig Zag, Windmill Alley, Snake Pass, The Slalom and the Grand Gold Star finale).

## Fresh start (update 2.3, Oct 28 2026)

Everyone started over (twice on Oct 28: once in the afternoon and again with update 2.3 at 7 PM ET). `RESET_EPOCH` is 3 (all progress, names, badges and homerooms wiped on every device and in the cloud), Leaderboard Season 6 (`SEASON = '_s6'`) started with empty all-time and daily boards, and `ACCT_EPOCH` logs every device out of its old account once so each golfer gets a brand-new player code. Old data stays in Firebase but the game ignores it (delete old users in Firebase console > Authentication > Users if you want it gone).

## Update 2.5 (Oct 29 2026)

- Smaller, quicker camera glide after each shot; teachers on the home screen stand still in low battery mode.
- Members stay signed in: the game remembers your member code and signs back in after a reload. Write your code down.
- Homeroom Cup: "Show all members" list for each homeroom, and **Continue match** after a reload mid-round.
- The game suggests low battery mode once.
- Only chamigolf1.firebaseapp.com runs the game: any other address (github.io, web.app) redirects there.
- Creator badge menu: ready-made creator badges or a custom one. Everyone sees 🎁 Creator's Pick; only the member sees their unique badge (custom details live in `giftInfo/{uid}`, readable only by that member).
- Mini golf hole 17 (The Slalom) rebuilt with clear gate openings and an aim line.

## Update 2.4 (Oct 29 2026)

- **Battery saver** (Golfer tab, `SAVER` in index.html): 30 fps (15 idle), pixel ratio 1, no shadows or anti-aliasing, no hole fly-in or camera glides (cuts straight to the golfer), no confetti, a still home screen. Switching it reloads the game.
- **Divots** behind iron and wedge shots off the turf (`addDivot`). **Aerial** button on every hole of a course page (a still render from above).
- **Golfer preview** stands still and is spun by dragging; it only redraws when something changes.
- **Icons** (`ICONS`, `ico()`) replace most emoji in the menus. Play tab cards: Play Friends, Closest to the Pin, Spirit Day, Driving Range (Practice), Leaderboards.
- **Homeroom Cup prizes** (`CUP_PAY`, `CUP_MVP_PAY`): every player in the 1st/2nd/3rd homeroom gets $2,500/$1,500/$750, and the best player of every other homeroom $750 (only when there's a winner). Paid once per week the next time the game is open after Friday 2:42 PM, from the saved final record (2 reads per golfer). The cup screen has its own navy-and-green look.
- **Anti-cheat**: every finished round is checked before it goes online (impossible hole scores, totals that don't add up, fewer strokes than swings, a round faster than 4 seconds a hole). A round that fails isn't posted and the creator gets a "not posted" flag (Creator tools > Flags). Saves edited by hand only send a note. Nothing bans automatically and nothing looks at the network or website address, so proxies are fine. The rules also check cup scores (18 under at most, par 54 to 76).

## Hole names (update 2.3)

Meribah, Brothers Hollow, Hearst Executive and Flyers Presidential use original, less corny hole names (`HOLE_NAMES` in index.html). The layouts didn't change.

## Spirit Day · Weekly Homeroom Cup

(Added Oct 28 2026.) Every week the 13 homerooms (A, B, C, D, E, F, G, H, J, K, L, M, N; there is no Homeroom I) play for the cup on one 18-hole course. The course rotates each week (Meribah, Brothers Hollow, Hearst Executive, Deans Valley, Chami Links Black) and everyone can play it, even if it's still locked for them (playing the cup doesn't unlock it).

- Pick a homeroom in the Golfer tab or on the cup screen (Play tab > Weekly Homeroom Cup). **It can never be changed** after you pick it. Golfer > Golf Bag > Logo has a free "HR" + letter tag for your bag.
- Your official score is your best full 18-hole round on the cup course from **Monday 7:00 AM to Friday 2:40 PM** (Eastern). Every finished round counts as an attempt.
- A homeroom's **team average** = the average of its **20 lowest** official scores (all of them if it has 10 to 19). Under 10 valid scores = **Not Qualified** (provisional average, can't win). Lowest average wins.
- **Ties** (at the 20-player cutoff and everywhere else) go to whoever posted that score first (the server's time stamp), then by player ID. Nobody can change either one.
- Screens: Teams (standings), Homerooms (one leaderboard per homeroom, with the 20 counting scores shaded light green and the team average, valid players, scoring positions, status, team rank and gap to the leader on top), School-wide (everyone, no shading) and Winners (podium of the homerooms with the most wins plus every past winner; tap a week for its final boards).
- Scores lock Friday 2:40 PM; the winner pops up for everyone at 2:42 PM. About an hour later the first game to open the cup saves the final standings to `hrcupWeeks/` (the history never changes after that). A new cup starts Monday 7:00 AM.
- Firestore: `hrcup/{monday}/scores/{uid}` (one row per golfer) and `hrcupWeeks/{monday}` (+ `/full/players`). Nicknames for homerooms can go in `HR_NAMES` in index.html. The cup's maths is one function, `cupCalc()`, used by every board, the green shading and the averages.

## Clubs and upgrades

- Each club has three upgrades, up to level 5 each: Power (+4% distance), Accuracy (+1.6% gold zone, and misses 8% straighter) and Control (needle 12% slower). Levels cost $400 / $900 / $1,800 / $3,500 / $6,000 (Power 20% more). A stat can only go one level past the club's lowest stat.
- Lots of club models to buy in every slot (more added Oct 28 2026: Blaze, Glacier and Phantom drivers, 7 Wood, 4 Hybrid, Wide Sole 6 Iron, Tour 9 Iron, 48° and 58° wedges, Tour Blade putter). Every driver has its own head colour. Club colours (buy a colour once, paint any club; Stock = the club's own colour).
- Shop prices are rounded to flat numbers (`flatPrice()` in index.html): $1,050 → $1,000 and so on.
- Customization is 30% off (Oct 20 2026): outfit colours, outfits, club colours, ball lines and the custom bag logo ($5,000, not part of the sale). `LOOK_SALE` in index.html sets the discount.

## Online

- Daily Tournaments for every course, mini golf and Closest to the Pin. No sign-in needed to post: you just need a name (anyone still called "Player" is asked for one).
- **Player codes (update 2.3):** every golfer gets an 8-character code like `ABCD-2345` automatically (no 0/O/1/I/L in new codes). Tap the 👤 player icon (top right) to see it, copy it, or **Log in** with a code from another device. No password, no email: under the hood it's a Firebase email/password account (`p-<code>@players.chamigolf.app`), so cloud saves, leaderboards and the rules work as usual. If an account can't be made right away (no internet, or too many sign-ups from one school network at once) the game uses a quiet guest account and tries again next time.
- **Google sign-in is gone completely.** The creator logs in with the creator's player code like everyone else; the creator tools and the rules recognise that account by its uid (`CREATOR_UID` in index.html, `isAdmin()` in firestore.rules). Never post the creator code anywhere public.
- Premium badges (Creator's Pick, Daily Champion, Hole in One) show next to your name on the leaderboards. Only the Creator's Pick tile shows how many golfers have it. Creator's Pick goes to golfers who helped make the game or had a suggestion added.
- Daily Champion counts your wins: the number of days you finished 1st (any Daily Tournament or Closest to the Pin) shows next to the 🏆, in the header, in the Golfer tab and next to your name on every leaderboard.
- Leaderboard Season 4 started Oct 20 2026: every board (all-time, daily tournaments, Closest to the Pin and holes in one) starts fresh. Old scores stay in the database but aren't shown. To start another season, change `SEASON` and `SEASON_START` in index.html.
- Unlockable outfits: the Senior Sweater (within 10 feet in the Daily Closest to the Pin) and the Green Jacket (par or better at Chami Links Black; it used to be called the Masters Outfit). The NHS Outfit is now the Gold Jacket. The Green Jacket's green and the Gold Jacket's gold (and close shades) can't be bought for a jacket on their own or mixed, so nobody can make a replica.
- Reloaded mid-round? Keep playing, finish the round early (paid for the holes you played), or quit.

## Play Friends

The Play tab card has one yellow **Browse match options** button that opens every option (1v1, 2v2, foursome, join with a match code).

- Sign in, create a match and send your friends the 6-character match code (or tap Share invite link in the lobby). Friend lists and friend codes were taken out on Oct 20 2026: everything is joined by code.
- **1v1**: stroke play for a wager ($0 up to what you have), 3, 6 or 9 holes. Tied? Sudden-death playoff holes.
- **2v2**: scramble, alt shot or best ball. **Foursome**: own ball (1v1v1v1, up to 4 golfers, lowest total wins the pot) or a 2 v 2 scramble. The host sets one buy-in that every golfer pays; a pop-up confirms it when you join, and you can't join without enough money.
- Everyone gets the same wind. Winners split the pot. Quitting a match forfeits it for your team.

## Bans, review lists and creator tools

(Rewritten Oct 27 2026: the old automatic anti-cheat was banning real golfers by mistake.)

- **The game never bans anyone by itself.** Only the creator can ban (🛡️ creator tools). Every old automatic ban (`auto: true` in `bans/`) is ignored by every game and by the rules, and the creator's game deletes them the next time the creator tools are opened, so everyone who was auto-banned can play again.
- **Appeals are gone**, and so are the automatic cheat flags and the money watchdog.
- **Holes in one are still logged**: every ace is a flag (kind `ace`) with the golfer's career total, club, swing and the card so far. 🎯 Holes in one and 🎯 Ace flags in the creator tools list them.
- **📋 Scorecard review**: the full scorecard of every round of **-9 or better over 9 holes** or **-18 or better over 18** (one under per hole on other lengths) goes to `reviews/`. Look it over, then ✓ Looks fine, 📋 All cards or Ban.
- **Banned golfers are taken off every leaderboard**: their scores are deleted (all-time, the last week of daily tournaments and Closest to the Pin) and a small banned list (`meta/bannedList`) hides them from every board, the tournament leaders and the prize payouts.
- **Server side (firestore.rules)**: only you can write your own save, scores and review cards; the cloud bank can never be more than $5,000 over everything earned; scores and names are range-checked and filtered; score times must be within 2 days of now; boards only accept a better score; banned golfers can't post; only the creator's account can ban, unban, delete scores or give badges.
- The creator's account (🛡️ button on the home screen) has Find a player (search by name, give or take back Creator's Pick 🎁, ban), 🎯 Holes in one, 📋 Scorecard review, 🎯 Ace flags, ⛔ Bans (with 📋 scorecards) and the leaderboards (remove a score, ban, 🎁).
- Player counts, players online and rounds played are in Google Analytics.

## Updates and pop-ups

- To announce an update to players, edit `NEWS_VER` and the `NEWS` list in index.html. Each golfer sees it once. Only list things players can see (nothing about anti-cheat or creator tools).
- **Every release:** bump `GAME_VER` in index.html and `"game"` in `version.json` to the same value (and `"news"` / `"num"` to match `NEWS_VER` / `NEWS_NUM` when there's a What's New). Games that are already open check `version.json` every 5 minutes and when the player comes back to the game, then show an "🔄 Update ready · Reload now" pop-up on the home screen (never mid-round). Add each update to the `UPDATES` list too (the "📜 Previous updates" page).
- New players get a welcome pointing them to the 3C Par Three, plus one-time tips the first time they open Clubs and Golfer.

## Firebase free plan

The game is built to stay on the free Spark plan (50,000 reads and 20,000 writes a day; on Spark Firebase never charges, it just pauses online features until midnight Pacific if a limit is hit):

- Cloud saves (Google sign-in) go up only when a round ends, after buying something or collecting winnings, and when the game is closed. The device always saves instantly.
- Leaderboards are remembered for 5 minutes, even through a reload. Your own new score is added to the remembered board instead of downloading it again, and posting skips the "current best" lookup.
- Today's tournaments card only loads when someone taps "See today's leaders" (then it's remembered for 10 minutes).
- Today's holes-in-one are one record per day (the creator tools read the last 3 days).
- The banned list is one record (1 read per visit, remembered for 30 minutes).
- The Creator's Pick count loads once per visit; the ban check runs every 15 minutes.
- Play Friends is joined by match code only (no friend codes or invite inbox to watch). Stroke play and best ball send one score per hole; scramble and alt shot send every shot because players take turns.
- Cloud saves check for newer progress at most once a minute when you come back to the game (1 read).
- No "last seen" notes or daily counters: those stats come from Google Analytics.
- The creator's Find a player search uses a tiny player directory: one record per golfer, written only when they first pick a name or change it.

## Google Analytics

On, with Measurement ID `G-4D02FQ9XMJ` (`GA_ID` in index.html). Players online, players per day, new players, rounds started and finished, aces and Closest to the Pin shots show up in Google Analytics (Firebase console > Analytics, or analytics.google.com). It's free and doesn't count against Firebase's database limits.

## Firebase setup

1. Publish the rules in `firestore.rules` (Firebase console > Firestore Database > Rules > Publish). **Publish them again for update 2.2 (Oct 28 2026)**: it adds the Weekly Homeroom Cup (`hrcup/`, `hrcupWeeks/`). Until you do, cup scores can't be posted.
   **Also for 2.2: turn on player codes:** Firebase console > Authentication > Sign-in method > **Email/Password** > Enable (leave "Email link" off). Until you do, "Get my player code" shows an error. **Publish them again for update 2.1 (Oct 27 2026)**: it ignores old auto-bans, removes appeals and adds `reviews/` (Scorecard review). Until you do, golfers who were auto-banned still can't post scores and low rounds can't be sent for review. **Publish them again for update 2.0 (Oct 20 2026)**: it adds appeals, scorecards on cheat flags, the hard-ban mark and the Daily Champion win count. (Until you do, appeals can't be sent; scores and flags still post without the new fields.)
2. Sign-in methods: **Email/Password** (player codes) and **Anonymous** (the fallback guest account) must both be on. Google can be turned off.
3. Deploying: `firebase deploy --only hosting,firestore:rules --project chamigolf1` updates the site and the rules together (firebase.json points at firestore.rules).

ChamiCards will be back.

## Hosting on Netlify

GitHub Pages and Vercel are blocked on some school Wi-Fi, so the game also runs on Netlify. `netlify.toml` serves the repo root as a static site (no build step, unknown paths load the game, the game and version.json are never cached).

1. netlify.com > **Add new site** > **Import an existing project** > **GitHub** > pick **ChamiGolf/chamigolf.github.io** > **Deploy** (leave the build command empty and the publish directory as `.`; netlify.toml sets both).
2. Copy the new `something.netlify.app` address (Site configuration > Change site name to pick a nicer one, like `chamigolf.netlify.app`).
3. Firebase console > **Authentication** > **Settings** > **Authorized domains** > **Add domain** > paste the netlify.app address, so player codes work there.

Every push to the repo redeploys the Netlify copy automatically.

## License

MIT
