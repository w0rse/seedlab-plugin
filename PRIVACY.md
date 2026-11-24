# Seed Lab: privacy policy

Last changed on 24 November 2026. Every change to this page is in this repository's history.

This page covers the Seed Lab plugin for Claude and the Seed Lab connector it talks to, at `https://w0rse.xyz/seedlab/mcp/data`.

## Who runs it

Seed Lab is a personal project, not a company. It is run by the owner of the GitHub account that publishes this repository. To ask a question about this policy or about your data, open an issue at https://github.com/w0rse/seedlab-plugin/issues. Issues are public, so say only what you are asking for; if the details are private, say so and you will be given a private way to send them.

## What the plugin does on your machine

The plugin is a set of instructions for Claude and the address of the connector. It runs no program on your machine, sets no cookie, has no analytics and no telemetry, and reads nothing by itself. Claude, working in your project, decides what to send, as described below.

## What the connector receives

**A description of your page**, when Claude asks for directions. Claude writes it: what the product is, who the page is for, what kind of page it is, what people come to it to do, the problem to solve, what must keep working, and a short account of what is on the page. Your code and your files are not sent.

**Screenshots of your page**, when Claude asks for a review: up to 6 pictures, each at most 2 MB.

**What any web server receives with a request:** the internet address the request comes from, the time, and the name and version of the program that made it.

There are no accounts. The connector does not ask for a name, an email address or a payment, and does not receive them unless they are written into the description or shown in a screenshot. Keep secrets and other people's personal data out of both.

## What it is used for

The description is used to draw directions and, with the screenshots, to ask the design director for notes. The internet address is used to apply the limits that keep the service available: the connector turns it into a salted hash, keeps the hash in memory and in its log, and does not store the address itself.

Nothing you send is sold, used for advertising, used to build a profile of you, or used to train a model by Seed Lab. Descriptions and screenshots are not added to the Seed Lab experiment. The person who runs the server can read the stored descriptions while they exist, and reads them only to fix a fault or to stop misuse.

## Who else receives it

**OpenRouter, and the vendor of the design director's model.** When a review is asked for, the screenshots and the description are sent to the design director, a model from a vendor other than Anthropic (by default `openai/gpt-6.1-terra`, from OpenAI), through OpenRouter. Your internet address is not sent with them, and nothing that identifies you is added. What these companies keep, and for how long, is set by their own policies (https://openrouter.ai/privacy and https://openai.com/policies), not by Seed Lab. Claude is told to say this to you before the first review. Nothing is sent to them if no review is asked for.

**The hosting company.** The connector runs on a server rented from Hetzner Online GmbH, in Germany. The stored descriptions and the logs are on that server.

**Google, only if you ask for new typefaces.** The page Claude builds then loads two typefaces from Google Fonts, so the browsers of people who open that page will ask Google for them. That is a property of the page in your project, and you can remove it.

**GitHub**, if you open an issue.

No one else receives anything.

## How long it is kept

| What | Where | For how long |
| --- | --- | --- |
| The description of your page, with the directions drawn for it and their colours | A file on the server | 30 days after it was last used, then deleted |
| Screenshots | A file on the server | Deleted as soon as the design director has answered. One that is never reviewed can no longer be used after 30 minutes, and is removed the next time the server clears expired uploads |
| The connector's log: the time, the tool called, the salted hash of the address, the id of the direction, the size of an upload | The server's system journal | Until the journal, which has a fixed size, overwrites it: days to weeks |
| The web server's access log: the internet address, the time, the request, and the name of the program that made it | A file on the server | About a week: the log is rotated daily and seven old files are kept |
| How many reviews were made today | A file on the server | Until the next day |

The salt of the hash is made anew every time the connector starts, so a hash cannot be matched to an address, or to an earlier hash, after a restart.

## Your choices

- Everything except the review works without sending a screenshot. If a page shows anything that must not leave your machine, tell Claude to skip the review.
- A description is deleted without your doing anything, 30 days after it was last used. To have one deleted sooner, open an issue with the id of the direction (eight letters and digits, such as `abcdefgh`); the id says nothing about the page.
- Uninstalling the plugin ends all contact with the connector.

## Children

Seed Lab is a tool for people who build web pages. It is not meant for children and is not directed at anyone under 18.

## Changes

When the connector, the server it runs on or the companies it sends to change, this page is changed in the same commit as the plugin, and the date at the top with it.
