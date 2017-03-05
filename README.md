# rvt_model_services
tools to process actions on revit models from cli

##it requires/is currently run on:
  * cpython >= 3.5 (with non-standard modules: docopt, numpy, pandas, bokeh)
  * [revitpythonshell](https://github.com/architecture-building-systems/revitpythonshell)
  * Autodesk Revit®

##how it works:
  * you initialize it with a command to process_model.py specifying the task, project path and revit version and a timeout.
  * process_model.py will spin off a subprocess to write a journal file and addin according to your specified task and project.
  * it will then run Revit according to journal file, opening a detached version of your model and run the specified action which in most cases will be [revitpythonshell](https://github.com/architecture-building-systems/revitpythonshell) script.
  * if the journal file cannot be run to completion the subproces is killed and an error is logged.

##typical use cases(typicially recurring tasks run via schedule Task Scheduler):
  * extraction of qc data to be gathered in csv table and visualized on interactive html graphs using bokeh 
  * check on model corruption with audit canary
  * export of DWF, DWG, PDF or IFC (so far only DWF export implemented)

##currently implemented tasks:
  * qc: rvt model qc statistics
  * dwf: dwf sheet exports of sheet set "Auto_PDF_DWF"

##limitations (typical limitations a journal file run process typically has):
  * no white spaces in model path
  * no non-ascii characters in model path
  * task will not run to completion if confronted with any unexpected messages

##credits

 * Frederic Beaupere (original version, maintainer)
 * Daren Thomas (creator of [revitpythonshell](https://github.com/architecture-building-systems/revitpythonshell))
 * Ehsan Iran-Nejad (creator of [pyRevit](https://github.com/eirannejad/pyRevit))
 * Gui Talarico (creator of [revitpythonwrapper](https://github.com/gtalarico/revitpythonwrapper) and [revitapidocs](https://github.com/gtalarico/revitapidocs))

note: If you are not on this list, but believe you should be, please contact me!
