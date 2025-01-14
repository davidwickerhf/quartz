## ✏️ uncompleted tasks
```dataview
TASK
FROM "Agenda/Daily"
WHERE !completed AND file.day.month = date("lecture-01").month AND !contains(tags, "#habit") AND !rescheduled
GROUP BY file.name
```

## ✅ habit tracker

```dataviewjs
dv.span("**📚 Reading**")

const calendarData = {
    year: 2024,
	blue: ["#ffdf04","#ffbe04","#ff9a03","#ff6d02","#ff2c01"],
    entries: [],
    intensityScaleEnd: 45
}

for(let page of dv.pages('"Agenda/Daily"').where(p=>p.reading)){
    calendarData.entries.push({
        date: page.file.name,
        intensity: page.reading,
        content: await dv.span(`[](${page.file.name})`),
    })
       
}

renderHeatmapCalendar(this.container, calendarData)
```

```dataviewjs
dv.span("**🏃‍♂️ Running**")

const calendarData = {
    year: 2024,
	blue: ["#ffdf04","#ffbe04","#ff9a03","#ff6d02","#ff2c01"],
    entries: [],
    intensityScaleEnd: 45
}

for(let page of dv.pages('"Agenda/Daily"').where(p=>p.run)){
    calendarData.entries.push({
        date: page.file.name,
        intensity: page.reading,
        content: await dv.span(`[](${page.file.name})`),
    })
       
}

renderHeatmapCalendar(this.container, calendarData)
```

```dataviewjs
dv.span("**🧔‍♂️ Beard care**")

const calendarData = {
    year: 2024,
	blue: ["#ffdf04","#ffbe04","#ff9a03","#ff6d02","#ff2c01"],
    entries: [],
    intensityScaleEnd: 45
}

for(let page of dv.pages('"Agenda/Daily"').where(p=>p.microneedling || p.beardcream)){
    calendarData.entries.push({
        date: page.file.name,
        intensity: page.reading,
        content: await dv.span(`[](${page.file.name})`),
    })
       
}

renderHeatmapCalendar(this.container, calendarData)
```

```dataviewjs
dv.span("**🚿 Shower**")

const calendarData = {
    year: 2024,
    entries: []
}

for(let page of dv.pages('"Agenda/Daily"').where(p=>p.shower)){
    calendarData.entries.push({
        date: page.file.name,
        content: await dv.span(`[](${page.file.name})`),
    })
       
}

renderHeatmapCalendar(this.container, calendarData)
```

```dataviewjs
dv.span("**🛌 Linen Change**")

const calendarData = {
    year: 2024,
    entries: []
}

for(let page of dv.pages('"Agenda/Daily"').where(p=>p.linen)){
    calendarData.entries.push({
        date: page.file.name,
        content: await dv.span(`[](${page.file.name})`),
    })
       
}

renderHeatmapCalendar(this.container, calendarData)
```

# 📝 notes calendar
```dataview
CALENDAR file.mtime
WHERE !contains(file.name, "lecture")
```