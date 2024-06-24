<%*
  const baseFolder = tp.date.now("[/journal/]YYYY[/daily/]MM[-]MMM/")
  const datePart = tp.date.now()
  
  if ( tp.file.title.startsWith("meetings") ) {
    const noteType = "meetings"
	const newFilename =  baseFolder + noteType + "/" + noteType + "-" + datePart
    //await tp.file.move(newFilename)
    tR = await tp.file.include(`[[_templates/daily-${ noteType }-template]]`)
  }
  
  if ( tp.file.title.startsWith("issues") ) {
    const noteType = "issues"
	const newFilename =  baseFolder + noteType + "/" + noteType + "-" + datePart
	tR = await tp.file.include(`[[_templates/daily-${ noteType }-template]]`)
  }
  
  if ( tp.file.title.startsWith("daily") ) {
    const noteType = "daily"

	tR = await tp.file.include(`[[_templates/worklog-time]]`)
  }
  
_%>