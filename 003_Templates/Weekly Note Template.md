---
banner: "![[weeklynotesbanner.png]]"
banner_y: 3
---
*Credit to u/ruetanissed, Change is tomorrow*

# <% tp.date.now("YYYY-MM [Week] WW") %>

[[<% tp.date.now("YYYY [Week] WW", -7) %>|↶ Previous Week]] | [[<% tp.date.now("YYYY [Week] WW", 7) %>|Following Week ↷]]

> [!METADATA]-
> Created:: [[<% tp.date.now('YYYY-MM-DD') %>]] <% tp.date.now('HH:mm') %>
> Updated:: <% tp.date.now('YYYY-MM-DD HH:mm') %>
> ID:: <% tp.date.now('YYYYMMDDHHmmss') %>

**Table of Contents:**
```toc
style: number
```

___

## Memos
- **[[<% tp.date.weekday("YYYY-MM-DD", 1) %>|]]**
	![[<% tp.date.weekday("YYYY-MM-DD", 0) %>#^memo-link]]
- **[[<% tp.date.weekday("YYYY-MM-DD", 2) %>|]]**
	![[<% tp.date.weekday("YYYY-MM-DD", 2) %>#^memo-link]]
- **[[<% tp.date.weekday("YYYY-MM-DD", 3) %>|]]**
	![[<% tp.date.weekday("YYYY-MM-DD", 3) %>#^memo-link]]
- **[[<% tp.date.weekday("YYYY-MM-DD", 4) %>|]]**
	![[<% tp.date.weekday("YYYY-MM-DD", 4) %>#^memo-link]]
- **[[<% tp.date.weekday("YYYY-MM-DD", 5) %>|]]**
	![[<% tp.date.weekday("YYYY-MM-DD", 5) %>#^memo-link]]
- **[[<% tp.date.weekday("YYYY-MM-DD", 6) %>|]]**
	![[<% tp.date.weekday("YYYY-MM-DD", 6) %>#^memo-link]]
- **[[<% tp.date.weekday("YYYY-MM-DD", 0) %>|]]**
	![[<% tp.date.weekday("YYYY-MM-DD", 0) %>#^memo-link]]

## Overview
### Week Statistics
```dataviewjs
const daysPath = dv.current().file.folder;

const attributes = {
	'panic': {
		label: 'Panic',
		average: 10,
	},
	'money-spent': {
		label: 'Money Spent',
		backgroundColor: 'rgba(85, 174, 229, 0.2)',
		borderColor: 'rgba(85, 174, 229, 1)',
		average: 20,
	},
	'steps': {
		label: 'Steps',
		backgroundColor: 'rgba(141, 82, 188, 0.2)',
		borderColor: 'rgba(141, 82, 188, 1)',
		average: 10000,
	},
	'hours-worked': {
		label : 'Hours Worked',
		backgroundColor: 'rgba(143, 208, 50, 0.2)',
		borderColor: 'rgba(143, 208, 50, 1)',
		average: 6
	},
};

const date = "<% tp.date.now('YYYY-MM-DD') %>";

customJS.DvCharts.renderWeeklyChart({
	dv,
	context: this,
	daysPath: '005_DailyNotes/<% tp.date.now("YYYY-MM-DD") %>',
	attributes,
	type: 'average',
	date
})
```

```dataview
TABLE WITHOUT ID
	link(file.name) as "Day",
	feeling AS "💭",
	money-spent AS "💸",
	panic AS "🌪️",
	steps AS "👣",
	hours-worked AS "✏️"
FROM "005_DailyNotes"
WHERE week = [[<% tp.date.now("YYYY [Week] WW") %>]]
SORT file.name ASC
```

### Habits
```dataview
TABLE WITHOUT ID
	file.link AS "Day",
	anki AS "📇",
	coffee AS "☕",
	exercise AS "🏋️",
	martial-arts AS "🥋",
	reading AS "👓",
	revision AS "🔁",
	shower AS "🚿",
	typing AS "⌨️"
FROM "005_DailyNotes"
WHERE week = [[<% tp.date.now("YYYY [Week] WW") %>]]
SORT file.name ASC
```

### Learnt Words
```dataviewjs
dv.table(
	["Learnt Word", "Meaning"],
	dv.pages('"005_DailyNotes"')
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




Tags: #personalnotes 
