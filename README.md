# Issue Stat Grabber

My TamperMonkey script that gets issue stats and puts them on your issues page.

## Usage
[Add the script](https://github.com/Kractero/issue-stats/raw/main/issueStatGetter.user.js) to Tampermonkey.
In the getBadgeMap function at line 39, add your identification means in lieu of the curly braces.

If you want to build your own issues_list.json, make sure you have Python on your system.

```
git clone https://github.com/Kractero/issue-stats.git
pip install -r requirements.txt
python generate_json.py
```

---

## Known Issues

Please file an issue if you run into any bugs, because there will be bugs.

I am working on mitigating issues and manually fixing, but one that will be difficult to fix will be missing text/results. This is because I am relying on multiple parties to have their data correct, these being MWQ and the Valentine Z megathread. With being MWQ being updated very often, I believe almost all the issues come from the megathread being out of date, but since choices are the only thing the script is able to get from NationStates, nothing can really be done about it unless I make a PR. I manually corrected to the best of my ability but until the megathread is updated, there may be some issues.

This means that some stats may be stale, as MWQ's mean stats change very often (but not enough to really matter).

---

![Issue Result Sample](/public/Issue%20Result.png)

## Features

1. See MWQ results directly on your issue pages, no more hopping between tabs or windows.
2. Select the categories relevant to the nation you are in, and store each nation's configuration in local storage.
3. Quickly toggle all, one percent, five percent, ten percent, and unranked badges with one button.
4. See your exact badge icons alongside the results and regenerate them if they are out of date with one click.

![Filter](/public/Filter.png)

---

## Legality
I believe that this script falls within the rules of the "
Script Rules for HTML site", as this script makes zero restricted actions and just scrapes information at the max.

--- 

## Contributing
Contributions are welcome, especially to the json generation script. Just make a PR.

---

### Dev Notes
I care about the stats on a select few of my puppets, and I became tired of flipping through MWQ and NSIndex for issues to pick the right choice, sometimes even tanking stats because of mismatching the numbers and the actual issue choice. I then had the idea to make a TamperMonkey script that would inject MWQ results onto the issues page.

Initially, this was to be an edge function route (mainly for personal use), and this was because of CORS, which would prevent me from getting both NSIndex and MWQ data. It would then scrape MWQ Issue results (a data repository by Trotterdam) and NSIndex (a now read-only wiki by Minoa), and would use the two to map the issue choices presented by a nation to the issue choices from NSIndex and effect lines and results from MWQ. This worked relatively well and can be seen in earlier commits and most of the current code is adjusted from this era.

Sherpdawerp made me aware of an unfinished python script they made that would generate a json based off the issue megathread. I was aware of the issue megathread but it did not seem easy to map its large and inconsistently formatted issues to MWQ, but using their script as a springboard, I finished it and made it more robust to account for megathread edgecases and added the MWQ feature that was yet to be added. I then installed these jsons in place of NSIndex and MWQ and continued to use the edge solution. I added fastify around this time so people could potentially self host it.

I then realized that since the only fetch calls left were to github's raw.githubusercontent.com domain and nationstates itself, I was probably not going to run into any cors, so there was no point in having any api route at all. I then merged all the function into the TamperMonkey script, and that is where it is today.

Most of the core function is the same as when I was still scraping NSIndex and MWQ data, but this was an interesting journey and I have to thank Sherpdawerp for making me aware of their script.

### To Do:
Export local host stuff to local file so not all is lost after clearing browser data.