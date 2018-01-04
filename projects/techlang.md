


type
- box/json
- - open, temp box, mock, pending, 
- - closed, saved box, persisted, log, db/api-backed
- - - common schema.org complex types
- - - apis, ifttt, google, etc
- - archived boxes, these no longer have active tests, there data is sealed, these archived boxes can then be deleted by GC later
- data (text/var/dynamic)
- - markdown-ish
- - html
- - - xml
- - config
- - code
- - - comment
- - - function
- - - - action, command
- - - - - batches, transactions of commands
- - - - rules, tests (comparison to produce a check), can act as alerts
- - - - definition
- - - - - alias, a reference to a definition which itself becomes a definition
- - number
- - - integer
- - - fast-integer
- - - - check (bool)
- - id/guid
- - label, a type attached to a box
- 

also part of all types
- aliases, which other labels, these also act as pointers to the box (find all references)
- comments
- rules/tests
- functions  (that take it as first param)


rules
if this then that
if x then x + 1
but also for maps/dicts
if 'this then 'that (conditions)


(comments)

[boxes]
{labeled boxes: boxes with specified definitions by ids}

'definition: 
you dont need to give things names as labels
types are sufficient
or don't give it any kind of label, but then you cant reference it

you can include comments in labels and they are just for the dev, not used in import/export, but are used for automapping


the deepest boxes are rooms and these are the environments, dev, prod, etc
ui has 3 main areas, each a room
- code browser, which includes blue things, closed/peaked boxes, these can be opened locally to pin
- - data definitions
- - box definitions
- - code definitions
- - worker definitions
- - standard definitions, docs
- actions, which include open boxes, these are at the top
- - repl/scratch, 
- - editor commands, like acme
- - all saving, all changes are done here
- output of each

^^ this should really be a tree with commands/repl at the top


you can have lots of data  with no labels, labels appear on the left
labels have color codes


red = core problem
orange = something is wrong, there is now a problem, requires fixing
yellow = something might not be ok,  perhaps is causing red/orange somewhere else, or related to it, possible active changes going on, perhaps it needs tests, more info, 
gray = something is ok, pending/processing, locked, not yours at the moment, not good yet though, possibly stale
green = something is good, but not live yet, box is open
blue = something is running live, box is closed or peaked

blue code is running
you can copy it, to make it green and able to make changes
as you make changes, it turns yellow
as you add tests to verify things are good, then things turn good
only green things can become blue

purple might be something noteworthy in live, maybe a received PR or an alert, pushes, new data


you can't make changes to live (prod) data directly at all
you can run queries, and use current code as input to functions
but you can make changes to temp data as much as you want
all changes to data require liquibase-like commands and tests
all changes to code require liquibase like commands and tests

everything has to have proper syntax all the time
so opening a brace, immediately creates a close brace
if you want to surround something existing, then there is a command for that

unit tests need to pass before it gets moved from dev to prod
if there is an error, it becomes a bug, and bugs require a reproduction test in the form of a unit test and then the unit test must pass
you can not just complete rewrite the project without starting a new project and copying in

every new project is a dead simple api and web controller with db and tests and continuous delivery

branches and merges are built in as
each repl is its own branch of code
opening a box is a copy, a clone, a branch
closing a box commits any changes to the contents, you can see who else has boxes open
peaking in a box is a live preview, not a copy, not yet opened
everything can be peaked into

but closing things are done in transactional commands, at once, and these require review, PRs
even if only yourself is the reviewer, you get a diff and you go through each change confirming it, and then a final approve/merge to commit

the blue system itself, is in blue, and is able to be peaked (inspected and copied), but changes can't be closed back into the sytem unless you have permissions


data +

code +


shared cloud service
like nrepl
like sharepoint
like ipython notebook
like github+travis+appengine
like 80s smalltalk goals
pending stuff in browser cache, and you can work on somethings just in cache, locally
