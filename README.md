# project_peak_demand
Peak Demand: How one Hudson Valley town blocked a 1-gigawatt data center

This is a data journalism project I built as part of the Lede Program at Columbia University. 

Data center pushback is spreading nationwide, from statehouses to town halls. It's not just in the headlines but happening near where I live. It's a deep dive into a small town's fight against one of the largest data center proposals in New York state, and how it ended in a unanimous vote to stop it.

Read the story here: https://liyanziqia.github.io/project_peak_demand/

# Question:  A quick eyeballing of social media posts and local media reports indicated concerns over rising power bills and strained resources. Is that the case, or local residents have other concerns? 


# The data

Sources: YouTube auto-generated transcripts of East Fishkill Town Board meetings (EF22NY channel); Central Hudson Gas & Electric's published residential rate history; U.S. EIA average household electricity consumption figures.

I pulled four meeting transcripts (March–June 2026) via YouTube's transcript API, then ran keyword frequency and co-occurrence analysis in Python to identify recurring terms and phrases. Central Hudson's own published rate history (2016–2025) was used to calculate the rate and bill-increase figures. The 1.3-million-household comparison is a scenario calculation, not a reported figure, built from the proposal's stated 1 GW capacity and EIA's average NY household usage.

One limitation: I could not find a New York state average electricity rate that was strictly comparable to Central Hudson's own rate structure, which limited how far I could take the "is this town paying more than the rest of the state" comparison.

# What I found

A New Jersey-based developer submitted an interconnection request to the New York Independent System Operator (NYISO) in 2025 to evaluate the grid impacts of a proposed 1 GW (1,000-megawatt) data center on wooded parcels in East Fishkill that had previously been considered for warehouse development. Local residents didn't learn about the plan until May 2026. Word-frequency analysis of four Town Board meetings shows the town's attention spiking sharply in the weeks that followed, from zero mentions of "data center" in March to 195 by the June 25 meeting where the board voted unanimously to block new data center construction for three years.

That tension unfolded against already-rising electric bills: Central Hudson's average residential rate climbed 86% between 2016 and 2025, and residents are set to see another $6.25 added to their monthly bill this year.

To put the scale of the proposal itself in context: at full capacity, a 1 GW facility would draw an estimated 8.76 billion kilowatt-hours a year, equivalent to the electricity usage of nearly 1.3 million average New York households.

# What's in this repo

Notebooks: I used several jupyter notebooks for this project:
1. Scraping_youtube: to fetch transcripts
2. Power_center: the original notebook I started with before I realized that the New York state power rates I calculated are not really comparable to the local rates
3. Power_center_CORRECTED: this is the main notebook that I used throughout the project to document the learning process. I had to re-work on entire section about power rates but I kept both notebooks to remember the mistake.
4. ego_cloud_phrases: our nice TA helped me get a headstart with a text analysis to generate a word cloud image. She walked me through the process, which I really appreciate. 
Other files: CSV files: all the dfs I saved, including the raw transcripts and power rates. Images: the word cloud image and the line chart. Eventually, the html file, which I included a D3 animation practice 


# How I worked

Step 1, Identify: I built a timeline of the East Fishkill proposal from local news coverage, to establish which four Town Board meetings  actually discussed it, before scraping anything.

Step 2, Fetch: I pulled transcripts for those four meetings via YouTube's transcript API (no video downloads required), and Central Hudson's residential rate history directly from the utility's own published PDF.

Step 3, Clean: I spent a lot of time on updating the stop words, or words that don't really mean anything in this context, such as "more," and "applause", as well as setting and resetting the "window". Plus, auto-generated captions strip apostrophes (turning "don't" into "don t"), which I corrected with a regex-based fix before running any word analysis, otherwise contractions like "don't want" would have silently broken apart into meaningless single words.

Step 4, Analyze: I ran keyword frequency counts and co-occurrence analysis (including negation phrases like "don't want" and "cannot afford") to trace how concern about the proposal built up across the four meetings, then manually verified the strongest quotes against the original video before using them. For sanity check, I manually checked some of the examples of the quotes. 

Step 5, Visualize: I built a word cloud (highlighting "moratorium" against a muted palette) and a rate-history line chart from the verified data, plus an animated stat callout using D3 to show the 1.3-million-household comparison. (super cool!)

Step 6, Story: I built the piece as a plain long-form HTML page rather than a heavily designed template, to keep the focus on the reporting rather than the visual design. I wanted to keep it clean. 


# What I decided NOT to include/abandon

I actually designed a fancy SVG image showcasing three scenarios of a 1 GW data center operating in different conditions: max capacity, downtime and overheating, and comparing them against the grid capacity. No, it didn't work. (Looking back it was one of the cases that I was overthinking and trying to squeeze several ideas into one thing)


# Tools used

Python (pandas, re, youtube-transcript-api, wordcloud, altair)
YouTube Transcript API
U.S. EIA household electricity data
D3.js (stat animation)
Jupyter Notebook


# AI use note

I used AI to help debug the codes back and forth, especially when building the basic html template, my first webpage design. 


# Questions or corrections

If you spot an error, please get in touch.