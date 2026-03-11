## Background

About a year ago, a few months into my new job, we started working on a report about the **company landscape on the Norwegian Continental Shelf (NCS)**. The goal was simple: to understand what kinds of companies operate on the NCS today and how this has changed over the last 10–20 years. Who explores? Who produces? Which types of companies dominate at different times?

[The report was published a year later, in December 2025, and was very well received.](https://www.sodir.no/aktuelt/publikasjoner/rapporter/aktorbildet-2025/)

Early in the process, I wanted to build a mental map of the industry myself. As someone new to the sector, I needed a clear overview: **which companies operate on the NCS today, and which ones were here 10–20 years ago?**

The answer turned out to be surprisingly complicated.

In the mid-2000s there were roughly **30 companies** active on the shelf. That number grew steadily and peaked at **57 companies in 2013**. Since then, the number has declined again, reaching **23 companies in 2025**.

This change did not happen quietly. The industry has gone through wave after wave of **mergers, acquisitions, new entrants, and companies exiting the shelf**.

Tracking this is harder than it sounds. Companies merge, split, rename themselves, acquire assets, sell subsidiaries, or disappear entirely. None of this is designed to be easy to follow — especially if you are new to the industry.

After quite a bit of digging, I eventually built a spreadsheet mapping all these changes. Since 2000, there have been **around 110 different companies** involved on the Norwegian shelf. At any given time the number was much lower, but companies constantly enter, merge, disappear, and absorb each other.

Once that overview existed, the next question naturally followed:

**Could all of this actually be visualized in a single graph?**

## Typical charts for visualizing company consolidations

There are already several examples of visualizations that try to show consolidation in the industry. The challenge is that once you try to combine **company history**, **ownership changes**, and a **time dimension**, things get complicated very quickly. Most visualizations end up relying heavily on text to explain what is happening.

Personally, I try to avoid that whenever possible. In my view, a visualization should mostly speak for itself. If the reader has to read large blocks of text to understand it, the chart probably is not doing its job.

Here is an example from **Rystad Energy**, showing consolidation on the **UK Continental Shelf (UKCS)**.

![Rystad Energy — Company consolidation on the UKCS](/posts/company-consolidation-sankey/Rystad_Company_Consolidation.png)

*[Source: Rystad Energy research and analysis](https://www.spe-aberdeen.org/uploads/SPE_ICOTA_RYSTAD_AnyaAlbot_To_Share.pdf)*

As usual, Rystad has done excellent work. The visualization clearly communicates the consolidation history and gives a good sense of how companies have merged and disappeared over time.

But it also illustrates the problem I wanted to avoid: **a lot of text, labels, and company logos** are needed to make the chart readable.

A **Sankey diagram** requires more work to build, but it solves this problem much better. It allows you to show how companies flow into each other over time, while keeping the visual structure clean and easy to follow.

## Why Sankey diagrams are a perfect fit for complex consolidation history

Sankey diagrams are flow diagrams. They are ideal for showing processes step by step. People are very good at following lines and flows. — if something flows from one place to another, we intuitively understand it.

A good example is Apple’s income statement, which has been visualized as a Sankey diagram.

![Apple income statement as a Sankey diagram](/posts/company-consolidation-sankey/Sankey_Apple.png)

We immediately understand how the diagram works. Revenue streams like iPhone, Mac, iPad and Services flow into total revenue. As the flow moves to the right, costs, operating expenses and taxes gradually reduce the stream, leaving net profit at the end.

The entire income statement is still there — but instead of reading a table, we see it as a flow. The **width of the streams represents the amounts**, while the structure of the diagram shows how the numbers relate to each other.

This combination — **flow, structure and magnitude in one visual** — is exactly what makes Sankey diagrams so useful for showing company consolidations over time.

## Visualizing consolidation with a Sankey diagram and building the diagram

<iframe src="/posts/company-consolidation-sankey/Sankey_Diagram_DNO.html" width="100%" height="600" style="border:none;"></iframe>

Using a Sankey diagram we can trace the path of each company through time. Reading from left to right — the natural direction — it becomes easy to follow how companies gradually converge toward **DNO**. Along the way we can clearly see when companies enter the NCS, when two paths merge into a new entity, and when one company absorbs another.

Link and node widths are used to represent scale. Each company is assigned a value of **1**, so the width of each flow reflects how many predecessor companies are combined. For example, **Sval Energi**, which ultimately comes from six companies, appears with a link six times wider than a single-company flow. This makes it immediately visible which companies have grown through multiple acquisitions.

The color scheme in this prototype follows the **company category colors used by Sokkeldirektoratet** in the *Player Picture* report.  

Color can also be used differently. It can highlight market dynamics — for example showing companies **entering the NCS in green** and **exiting in red**.

This diagram is only a prototype. When working on the *Player Picture* report for Sokkeldirektoratet, published in December 2025, I built a much more comprehensive version of the same idea.

That Sankey diagram mapped **all active companies between 2018 and 2025**. The main focus there was changes in company categories, but the structure also made it possible to trace individual company histories.

Interactivity turned out to be particularly useful. By hovering or dragging across a node or category, the visualization highlights the full path connected to it. This makes it easy to isolate a single company’s history within a much larger network. Tooltips and highlighting add depth without cluttering the visual.

Here, the width of links and nodes becomes crucial again. Looking toward the right side of the diagram, it quickly becomes clear which companies had the biggest **acquisition appetite** during the period — most notably **DNO**, largely through the chain of companies that eventually became **Sval Energi**.

You can explore the visualization below. Try hovering over companies or categories to follow their paths through time.

<iframe src="/posts/company-consolidation-sankey/Sankey_Diagram.html" width="100%" height="600" style="border:none;"></iframe>

*Source: [Player Picture report, chapter 2 — Sokkeldirektoratet](https://www.sodir.no/aktuelt/publikasjoner/rapporter/aktorbildet-2025/utviklingen-i-aktorbildet/)*

## Challenges and lessons

The hardest part of building a good Sankey diagram is structuring the dataset correctly. The visualization itself is not the main challenge — the real work lies in organizing the underlying data so that every company, merger, and transition is represented in a consistent way.

This becomes especially demanding if you want features like **automatic node placement**, **time-series structure**, or **interactive highlighting**. Getting the data model right can take quite a bit of time.

Once the structure is in place, however, Sankey diagrams are very flexible. New companies, acquisitions, or time periods can be added without redesigning the entire visualization.

For this project I built my own Sankey implementation using a mix of **Python and JavaScript** to maximize flexibility and configurability. That said, there are many good libraries available, and it is entirely possible to build similar visualizations using existing packages.

If you have ideas for improving the **look of the diagrams** or the **process of creating them**, I would be very interested to hear them. Feel free to reach out by email.




