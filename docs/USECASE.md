## A typical Skyscraper use case
The following describes a typical way of using Skyscraper. It's really simple to use once you understand the core concept. It has a couple of layers you should familiarize yourself with in order to get the best results.

So let's dig in!

### You have some files and no data
You probably installed Skyscraper in order to get some data and artwork on your frontend game lists. So let's say that you have a bunch of Super Nintendo files you wish to populate with data.

![Skyscraper flowchart](https://raw.githubusercontent.com/muldjord/skyscraper/master/docs/skyscraper_overview_chart.png)

#### The gathering phase
Skyscraper can gather data from several scraping modules / sources (set with `-s <MODULE>`). So you'd start by scraping the `snes` platform (set with `-p <PLATFORM>`) with one or more of those modules. Each time you do so, all of the data will be saved in the Skyscraper cache.

```
$ Skyscraper -p snes -s screenscraper
```
This should have given you a lot of data for your games. But some of it might still be missing. So let's continue gathering some data from another module.
```
$ Skyscraper -p snes -s thegamesdb
```
For each of those two commands, all of the data that was gathered is now cached inside Skyscraper. For each game it will contain information from both of those sources.

#### The game list generation phase
And here comes the clever part. By having gathered data from both sources (`screenscraper` *and* `thegamesdb`) there's a good chance that you will get a complete result if the data from both is combined. And that's *exactly* what Skyscraper can do for you.
```
$ Skyscraper -p snes
```
Running that command will generate a game list for the chosen frontend (default is EmulationStation). It combines all of the cached data into the most complete results. This phase also includes the artwork compositing.

### So what then?
You're done! The platform has been scraped and you can relaunch your frontend to enjoy the newly scraped data and artwork. Or you can move on and scrape data for another platform. Just remember to distinguish between the *gathering* phase and the *game list generation* phase. Always gather first, then generate the game list afterwards. *Always!*

NOTE! You can always regenerate a game list if you changed the artwork configuration or gathered new data for any of your roms. Simply rerun the above command again and the game list will be regenerated from your new settings.

### But what about...
Yes, yes, yes. This is just the basics. You can customize the artwork completely to your liking. You can prioritize the different cached resources any way you like. You can scrape single games in order to gather information for just that one game. You can enable video scraping. You can import your own data into the cache. You can clean your cache. You can create aliases for games that are difficult to scrape. You can change your preferred region and language for the modules that support it. You can set up keys or user id's and password for the scraping modules that take advantage of this. There's *a lot* you can do if you want to.

The important thing to note is that the defaults for Skyscraper is set to work well for most users. So unless you see something you want to change, you don't have to. But it's equally important to know that you *can*.

If this piqued your interest, please read the entire documentation thorougly. Everything is documented to the last detail. It can seem overwhelming. But it gives you some really powerful options to scrape just the way you want. Read more about the advanced features [here](https://github.com/muldjord/skyscraper/blob/master/README.md#manual-mode-for-advanced-users)
