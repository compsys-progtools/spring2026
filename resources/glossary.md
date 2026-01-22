# Glossary

```{tip}
Contributing glossary terms or linking to uses of glossary terms to this page is eligible for [community badges](#community:defn)
```

:::::::{glossary}

absolute path
:  the path defined from the root of the system

add (new files in a repository)
:  the step that stages/prepares files to be committed to a repository from a local branch

argument
:  required input to a command in the shell 

base
: the shared {term}`commit` of a branch

base branch
: the branch that a PR or merg will add changes **into**

bash
:  `bash` or the bourne-again {term}`shell` is a popular interface in UNIX based systems
:  its code originally derived to be fully free an dopen source alternaive to the Bourne shell (`sh`)

bitwise operator
:  an operation that happens on a bit string (sequence of 1s and 0s). They are typically faster than operations on whole integers. 

blob
:  (in git) a type of git {term}`object` that contains the content of a file in a file named with the hash of the content

branch
:  an isolated version of the project in a repository where changes do not impact other changes
:  on github and other hosts [branches](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-branches) are used to create Pull Requests 
:  implemented with a pointer to a commit, that moves when new commits are added to the current branch

Bourne Shell
:  an early unix shell developed at Bell labs (`sh`)
:  the precursor to `bash`

command
:  an instruction given to a program
:  (informal) sort of like an individual function 

commit 
:  the basic unit of git

commit message
:  the plain language description that is required, entered with the `-m` option on `git commit`

compiled code
:  code that is put through a compiler to turn it into lower level assemlby language before it is executed. must be compiled and re-executed everytime you make a change.

detached head
:  a state of a git repo where the head pointer is set to a commit without a branch also pointing to the commit


directory
:  a collection of files typically created for organizational purposes

divergent
:  git branches that have diverged means that there are different commits that have same {term}`parent`; there are multipe ways that git could fix this, so you have to tell it what strategy to use

documentation ecosystem
:  the set of tools and syntax for creating, processing, and distributing documentation for a particular language

escape
:  (verb) to insert an <wiki:Escape_character>

exponent
:  (in floats) the part of the bitstring that is used as a power of 2 to scale the number
:  11 bits for 64 bit floats

fixed point number
:  the concept that the decimal point does not move in the number. Cannot represent as wide of a range of values as a floating point number.

flag
: another name for a single character {term}`option`

floating point number
:  the concept that the decimal can move within the number (ex. scientific notation; you move the decimal based on the exponent on the 10). can represent more numbers than a fixed point number.

fraction
:  (in float) the bits representing the fractional part of the number
:  also called the significand
:  52 bits for a 64 bit float

fork
:  a related repository, a full copy of the repo

git
:  a version control tool; it's a fully open source and always free tool, that can be hosted by anyone or used without a host, locally only.


GitHub
:  a hosting service for git repositories


.gitignore
:  a file in a git repo that will not add the files that are included in this .gitignore file. Used to prevent files from being unnecessarily committed.


git objects
:  see {term}`object`


git plumbing command
:  low level git commands that allow the user to access the inner workings of git.


git Workflow
:  a recipe or recommendation for how to use Git to accomplish work in a consistent and productive manner

hash
:  the output of a {term}`hash function`
:  (in git) the identifier for git {term}`objects <object>`


hash function
:  the actual function that does the {term}`hashing` of the input (a key, an object, etc.)


hashing
:  transforming an input of arbitrary length to a unique fixed length output (the output is called a hash; used in hash tables and when git hashes commits). 

HEAD
:  a file in the .git directory that indicates what is currently:  checked out (think of the current branch)

hidden file
:  a file with a name that starts with `.` that is not visible in default settings for file explorer/finder or with `ls` unless you use  `-a` 


integrated development environment
:  also known as an IDE, puts together all of the tools a developer would need to produce code (source code editor, debugger, ability to run code) into one application so that everything can be done in one place. can also have extra features such as showing your file tree and connecting to git and/or github.


interpreted code
:  code that is directly executed from a high level language. more expensive computationally because it cannot be optimized and therefore can be slower.


issue
:  provides the ability to easily track ideas, feedback, tasks, or bugs. branches can be created for specific issues. an issue is open when it is created. pull requests have the ability to close issues. see more in the [docs](https://docs.github.com/en/issues/tracking-your-work-with-issues/about-issues)

job
:  (in HPC) a set of work that will be run. 

Linker
:  a program that links together the object files and libraries to output an executable file.

markdown
:  a lightwight markup syntax that is human readable and parsable into HTML formatting [cheatsheet](https://www.markdownguide.org/cheat-sheet/)
:  see also  {term}`myst`

merge
:  putting two branches together so that you can access files in another branch that are not available in yours


merge conflict
:  when two branches to be merged have edits to the same line(s) preventing git from automatically merging the changes

myst
:  Markedly Structured Text, a flavor of {term}`markdown` designed to create publication quality documents in markdown, inspired by {term}`reStructuredText`

mermaid
:  mermaid syntax allows user to create precise, detailed diagrams in markdown files.

object
:  (in git) unit of storage in git, stored in the {term}`object database`, one of four types: commit, tree, tag or blob
:  (in git) identified by a hash, cannot be changed


object database
:  (in git) not a formal database, but a directory within a folder, that makes it a git {term}`repository` stores the git {term}`objects <object>`, generally found at the {term}`path`: `.git/objects`

one's complement
:  a representation where negative numbers are represented by flipping the bits

option
:  also known as a flag,
:  a parameter to a command line program that change its behavior, different from an argument

parent
:  (in git) the commit that came before the cuurent commit

path
:  the "location" of a file or folder(directory) in a computer

plumbing
:  (git command type) the internal workings- a toolkit for a VCS

pointer
:  a variable that stores the address of another variable

porcelain
:  (git command type) the user friendly VCS

pull (changes from a repository)
:  download changes from a remote repository and update the local repository with these changes.


pull request
:  allow other users to review and request changes on branches. after a pull request recieves approval you can merge the changed content to the main branch. (a [github feature](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests) that is also common to other hosts, not a git feature)


PR
:  short for {term}`pull request`

program
:  an installed piece of software; importantly distinct from an individual {term}`command`, e.g. git

prompt
:  the text displayed in the terminal before the content that you type
:  in bash, customizable with the environment variable `PS1`, see an example [helper tool](https://bash-prompt-generator.org/)


push (changes to a repository)
:  to put whatever you were working on from your local machine onto a remote copy of the repository in a version control system.

redirect
:  connecting the output of a command to an alternative {term}`stream`
:  syntax `>` for write mode and `>>` for append mode

ref
:  short for {term}`reference`

reference
:  (in git) a friendly name for accessing a commit, comes in three types: heads, remotes, and tags (which are also {term}`objects <object>`)
:  shortened to ref

relative path
:  the path defined **relative** to another file or the current working directory; may start with a name, includes a single file name or may start with `./`


release
:  a distribution of your code, related to a git tag


remote
:  a copy of the repository hosted on a server


repository
:  a project folder with tracking information in it in the form of a .git directory in it

reStructuredText
:  an plaintext markup syntax and parser system used for both inline documentation and creating websites and other types of documents [docs](https://docutils.sourceforge.io/rst.html)

ROM (Read-Only Memory)
:  Memory that only gets read by the CPU and is used for instructions


SHA 1
:  the hashing function that git uses to hash its functions (found to have very serious collisions (two different inputs have same hashes), so a lot of software is switching to SHA 256)

sh
:  abbr. see shell

shell
:  a command line interface; allows for access to an operating system

sign bit
:  a single bit used to indicate if a number is positive (0) or negative (-1)

significand
:  (in floats) another name for the {term}`fraction`

ssh 
:  allows computers to safely connect to networks (such as when we used an ssh key to clone our github repos)

STDOUT
:  standard output {term}`stream`


STDERR
:  standard error {term}`stream`

stream
:  a flow of data from one location to another in a computer 
:  includes three <wiki:Standard_streams>

tag
:  (in git) a {term}`object` that is like a branch in that it points to a commit, but also like a commit in that it is immutable and does not move. 

templating
:  templating is the idea of changing the input or output of a system. For instance, the Jupyter book, instead of outputting the markdown files as markdown files, displays them as HTML pages (with the contents of the markdown file).


terminal
:  a program that makes shell visible for us and allows for interactions with it


tree 
:  (in git) type of git {term}`object` in git that helps store multiple files with their hashes (similar to directories in a file system)


two's complement
:  a representation where to negate a number the bits are flipped and 1 is added to the number

yml
:  common file extension for {term}`YAML` files


yaml  
:  a file specification that stores key-value pairs. It is commonly used for configurations and settings.  [main docs](https://yaml.org/)


zsh
:  zsh or z shell is a {term}`shell` that contains new features that break conventions that `bash` adheres to but is faster at some things [see its FAQ](https://zsh.sourceforge.io/FAQ/)
:  a unix shell with a more permissive license (MIT) than `bash` (GPL)
:  a shell that is based on the KornShell (`ksh`) which was based on the Bourne shell initially

::::::::::
