# Scout: the round of Calls

I run this every two weeks. A round ends with at most about five Calls in front of me, each with a Talk to
bring and a new idea, and the Radar note updated.

## 1. The Radar note

Read "Radar Call" under the Conferenze hub `X8WYWSLmfXHr` ([SKILL.md](SKILL.md)): `## Regola`,
`## Watchlist`, `## Già viste`. Missing note or empty `## Regola`: stop and ask me for it.

Done when you hold the rule, the watchlist and every Call already seen.

## 2. Gather the Calls

Three sources plus one on request. Each **fails soft**: a source that is down, or whose shape changed, is
skipped with one line (`⚠ eventitech non risponde, salto`) and the round goes on. Filter with `jq` in a
temporary directory; the raw files run to megabytes, so only filtered lines reach you.

- **eventitech** (Italian, my main market; undocumented API, shape best-effort). A closing date of
  `0001-01-01` means no CFP:

  ```sh
  curl -sf -m 30 https://api.eventitech.it/api/v1/events | jq -c --arg today "$(date +%F)" '
    .events[] | select(.cfpClosingDate[:10] >= $today)
    | {name, start: .startDate[:10], end: .endDate[:10], city: .location, country,
       deadline: .cfpClosingDate[:10], call: .cfpUrl, homepage: .url, themes: .topics}'
  ```

- **developers.events** (Europe and what eventitech misses): open Calls from `all-cfps.json`, joined on
  the homepage to `all-events.json` for city, country and themes:

  ```sh
  d=$(mktemp -d)
  curl -sf -m 30 -o "$d/cfps.json" https://developers.events/all-cfps.json
  curl -sf -m 30 -o "$d/events.json" https://developers.events/all-events.json
  jq -c --argjson now "$(date +%s)000" --slurpfile ev "$d/events.json" '
    ($ev[0] | map({key: .hyperlink, value: .}) | from_entries) as $byurl
    | .[] | select(.untilDate > $now) | ($byurl[.conf.hyperlink] // {}) as $e
    | {name: .conf.name, start: (.conf.date[0]/1000 | strftime("%F")),
       end: ((.conf.date[-1] // .conf.date[0])/1000 | strftime("%F")),
       city: ($e.city // .conf.location), country: $e.country,
       deadline: (.untilDate/1000 | strftime("%F")), call: .link, homepage: .conf.hyperlink,
       themes: [($e.tags // [])[] | select(.key == "topic") | .value]}' "$d/cfps.json"
  ```

- **My watchlist**: fetch each Conference's CFP page and read whether the Call is open and until when.
  A page that says neither becomes a `da verificare` Call with its link.
- **Sessionize Discover**, only when I ask in this run: through the logged-in browser (Claude in Chrome).
  It is a fragile scrape: a lead to check, never a source of record.

Merge duplicates into one Call: the same Call link, the same homepage host, or the same name once year and
edition words are dropped, in the same city (Milano = Milan, Roma = Rome, Torino = Turin). Keep the richer
record and both links.

Done when every source either gave its open Calls or has its warning line.

## 3. Keep what is worth a look

Drop, in this order: Calls outside `## Regola`, Calls in `## Già viste` (same Conference edition), Calls
whose deadline is past. Sort the rest by deadline, soonest first, and keep about five. Online-only Calls
follow the rule like any other.

Done when you have the shortlist and the count of Calls the cap left out.

## 4. My Talks and what I'm on now

- **Talks**: every Talk note that is not archived ([SKILL.md](SKILL.md)): spark, `## Abstract`,
  `## Proposta`, the `## Talk` lines (where it has already been), and whether it has a Brief. Rank by
  cost to submit: published with a Brief first, then any Talk with a Brief, then one with an Abstract,
  then a bare spark.
- **Now**: my positioning in Aree/Pipeline contenuti `I78vgbZLZnde`, active Projects in Progetti
  `Gbou0FRbp5Ln`, Contenuti with `#status=in-progress`, and the content ideas in the Inbox
  `oI6dJqP0hGHG` (`#type=content #status=idea`): raw sparks, the best material for a new Talk.

Done when you can name, for each Call, the Talk that fits it best and why.

## 5. Propose

One block per Call, by deadline:

```markdown
### <Conference Year> · scadenza <YYYY-MM-DD>
<dates> · <city> · <themes> · <Call link>
**Talk**: <title> (<status>, <Brief / solo Abstract / solo spark>): <the angle to adapt it to this Conference>
**Nuovo**: <a Talk idea in one line, built on the Call's themes, my positioning and what I'm on now>
```

When the Talk has no Abstract, say so in its line (`match sullo spark, niente Abstract`). When nothing I
have fits, say it, and the new idea carries the block. End with the warnings from step 2 and how many
Calls the cap left out.

## 6. Decide

For each Call I answer one of:

- **invio** with an existing Talk: add its CFP line `CFP da inviare (scadenza …)` to that Talk's note,
  create-if-missing ([SKILL.md](SKILL.md)), then offer to answer the form now ([submit.md](submit.md)).
- **invio** with the new idea: go to [pitch.md](pitch.md) with the Call in hand.
- **scarto**, or nothing: it goes to `## Già viste`.
- **tienila**: it stays out of `## Già viste` and comes back next round.

## 7. Close the round

One write on the Radar note: every proposed Call except the kept ones appended to `## Già viste`, and
`**Ultimo giro**` set to today. Then run the outcome check in [outcome.md](outcome.md).

Done when the Radar note is updated and the outcome check has run. Reply with one line per decision.
