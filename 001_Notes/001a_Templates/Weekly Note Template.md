---
banner: "![[weeklynotesbanner.png]]"
tags:
  - personalnotes
---
# <% tp.date.now("[Week] WW") %>

[[<% tp.date.now("YYYY[-W]WW", -7) %>|↶ Previous Week]] | [[<% tp.date.now("YYYY[-W]WW", 7) %>|Following Week ↷]]

> [!METADATA]-
> Created:: [[<% tp.date.now('YYYY-MM-DD') %>]] <% tp.date.now('HH:mm') %>
> Updated:: <% tp.date.now('YYYY-MM-DD HH:mm') %>
> ID:: <% tp.date.now('YYYYMMDDHHmmss') %>

**Table of Contents:**
```toc
style: number
```
___
### Emotional Support Graph
```tikz
\usepackage{pgfplots}
\pgfplotsset{compat=1.16}

\begin{document}

\begin{tikzpicture}
\begin{axis}[colormap/viridis]
\addplot3[
	surf,
	samples=18,
	domain=-3:3
]
{exp(-x^2-y^2)*x};
\end{axis}
\end{tikzpicture}

\end{document}
```
---
### Tasks
```todoist
{
"name": "Unfinished this week(doo doo do do do)",
"filter": "7 days",
"sorting": ["date"]
}
```
---
## Memos
- **[[<% tp.date.weekday("YYYY-MM-DD", 0) %>|Monday]]**
	![[<% tp.date.weekday("YYYY-MM-DD", 0) %>#^dailynotes-link]]
- **[[<% tp.date.weekday("YYYY-MM-DD", 1) %>|Tuesday]]**
	![[<% tp.date.weekday("YYYY-MM-DD", 1) %>#^dailynotes-link]]
- **[[<% tp.date.weekday("YYYY-MM-DD", 2) %>|Wednesday]]**
	![[<% tp.date.weekday("YYYY-MM-DD", 2) %>#^dailynotes-link]]
- **[[<% tp.date.weekday("YYYY-MM-DD", 3) %>|Thursday]]**
	![[<% tp.date.weekday("YYYY-MM-DD", 3) %>#^dailynotes-link]]
- **[[<% tp.date.weekday("YYYY-MM-DD", 4) %>|Friday]]**
	![[<% tp.date.weekday("YYYY-MM-DD", 4) %>#^dailynotes-link]]
- **[[<% tp.date.weekday("YYYY-MM-DD", 5) %>|Saturday]]**
	![[<% tp.date.weekday("YYYY-MM-DD", 5) %>#^dailynotes-link]]
- **[[<% tp.date.weekday("YYYY-MM-DD", 6) %>|Sunday]]**
	![[<% tp.date.weekday("YYYY-MM-DD", 6) %>#^dailynotes-link]]
---
## Overview
### Week Statistics
```dataviewjs
const daysPath = dv.current().file.folder;

const attributes = {
	'panic': {
		label: 'Panic',
		average: 100,
	},
	'money-spent': {
		label: 'Money Spent',
		backgroundColor: 'rgba(85, 174, 229, 0.2)',
		borderColor: 'rgba(85, 174, 229, 1)',
		average: 100,
	},
	'hours-worked': {
		label : 'Hours Worked',
		backgroundColor: 'rgba(143, 208, 50, 0.2)',
		borderColor: 'rgba(143, 208, 50, 1)',
		average: 100
	},
};

const date = "<% tp.date.now('YYYY-MM-DD') %>";

customJS.DvCharts.renderWeeklyChart({
	dv,
	context: this,
	daysPath: '002_PersonalNotes/002a_DailyNotes',
	attributes,
	type: 'average',
	date
})
```
---
```dataview
TABLE WITHOUT ID
	link(file.name) as "Day",
	feeling AS "💭",
	money-spent AS "💸",
	panic AS "🌪️",
	hours-worked AS "✏️"
FROM "002_PersonalNotes/002a_DailyNotes"
WHERE week = [[<% tp.date.now("YYYY [Week] WW") %>]]
SORT file.name ASC
```
### Habits
```dataview
TABLE WITHOUT ID
	file.link AS "Day",
	Early_morning AS "🌅",
	Morning_shower AS "🚿",
	exercise AS "🏋️",
	reading AS "👓",
	revision AS "🔁",
	homework AS "📚"
FROM "002_PersonalNotes/002a_DailyNotes"
WHERE week = [[<% tp.date.now("YYYY [Week] WW") %>]]
SORT file.name ASC
```
### Learnt Words
```dataviewjs
dv.table(
	["Learnt Word", "Meaning"],
	dv.pages('"002_PersonalNotes/002a_DailyNotes"')
	.filter(p => p["Learnt Word"] && p.week.path == "<% tp.date.now("YYYY [Week] WW") %>")
	.sort(p => dv.date(p.file.name), 'asc')
	.flatMap(p =>
		Array.from(
			{
				length: Math.floor(
					p["Learnt Word"].length / 2
				)
			},
			(_, i) => [
				`${'**'}${p["Learnt Word"][i * 2]}${'**'}`,
				p["Learnt Word"][(i * 2) +1]
			]
		)
	)
)
```



