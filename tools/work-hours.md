---
name: work-hours
aliases: 
cssclass: 
tags: hours
category: None
subcategory: tools
create-date: 2024-06-24 21:06.00
update-date: 2024-06-24 21:06.37
---

#### Hours / Week

```dataviewjs
const tracked = {}
dv.pages('"daily/2023"').file.lists
  .where(x => x.section.subpath === "Worklog").array()
  .forEach(x => {
    // Find the start/end times for each bullet point
    //const times = x.text.match(/^(\d{2}:\d{2}) - (\d{2}:\d{2})/)
    const times = x.text.match(/^(.*:[0-5][0-9] [AaPp][Mm]) - (.*:[0-5][0-9] [AaPp][Mm])/)
    if (times) {
      // /(\d{4}\d{2}\d{2})/ - Works too
      const date = x.path.match(/(\d{8})/)[1]
      const week = moment(date).format('YYYY, [Week] WW')
      
      //const start = moment(times[1], 'HH:mm')
      //const end = moment(times[2], 'HH:mm')
      //const minutes = moment.duration(end.diff(start)).asMinutes()
      
      const start = moment(date + " " + times[1], 'YYYYMMDD hh:mm aa')
      var end = moment(date + " " + times[2], 'YYYYMMDD hh:mm aa')
      if ( start > end) {
	    //end = moment(date + times[2], 'YYYYMMDDHH:mm').add(1, 'days')
		//end = moment(date + times[2], 'YYYYMMDD hh:mm aa').add(1, 'days')
		end.add(1, 'days')
      } 
            
	  const minutes = moment.duration(end.diff(start)).asMinutes()
            


	  // Setup the week
      if (!tracked[week]) tracked[week] = {}

	  // Add up the date
      if (tracked[week][date]) {
        tracked[week][date].minutes += minutes
      } else {
        tracked[week][date] = {
        path: x.path,
        minutes: minutes
      }
    }
  }
})

const hours = minutes => (minutes / 60).toFixed(1)

const table = []
Object.keys(tracked).sort((a, b) => b.localeCompare(a))
  .forEach(weekDate => {
    // Push weekly value
    const week = tracked[weekDate]
    const weekTime = Object.values(week).reduce((prev, curr) => prev + curr.minutes, 0)
    table.push([weekDate, '**' + hours(weekTime) + '**'])

    // Push daily values
    Object.keys(week).sort((a, b) => b.localeCompare(a))
      .forEach(date => {
        const link = `– [[${week[date].path}#Worklog|${moment(date).format('dddd, D MMMM')}]]`
        table.push([link, '– ' + hours(week[date].minutes)])
      })
  })

dv.table(['Date', 'Hours'], table)
```