# Makefiles

A repository containing my notes on make files as well as a set of makefiles themselves demonstrating the results.

## Introduction:

​	Makefiles are files used to streamline the process of compiling and executing code, as well as cleaning up the working directory after. They are often used for compiling binaries and installing them on computers, and are therefore often used in open source projects to allow users to install said applications.

​	They are mostly used for C and C++. Other programming languages such as Java have their own compilation processes which are better suited to them. That said, they *can* still be used for said languages. Interpreter dependent languages, such as python may also potentially be compiled in this form if necessary.

## Makefile Creation & Execution:

​	Make files are made in two forms. First is the standard, in which the file is named **Markdown** or **markdown**. There are rare cases where the file is also named **GNUMarkdown** but this should be avoided unless the file requires the GNU make model. The second method of naming a make file is using the **.mk** file extension.

​	Make files are executed using the **make** command. A generic makefile can simply be executed as so:

```bash
make
```

However, if the makefile has a specific name, such as foo.mk , it must be run with the file argument provided as so:

```bash
make -f filename
```

or 

```bash
make --file filename
```

If only a certain part of the makefile has to be executed (Explained below in Syntax), then the name of the section must be provided as an argument without a specifier.

```bash
make section_name
```

## Syntax

​	All makefiles are divided into a function-like format which are labeled by key-words called targets. Each target is followed by a semicolon, which in turn is by a list of prerequisites. Each prerequisite in turn, is another target. This line is followed by an indented block of terminal commands to be executed if all the prerequisites are met. This looks like so:

```bash
target: prerequisite1 prerequisite2 ...
	command1
	command2
	.
	.
	.
```

### NOTE: INDENT MUST BE MADE WITH TABS, NOT SPACES

​	Make files are *extremely* sensitive to whitespaces. A makefile indented with spaces *will not run*. This is also true for trailing spaces, i.e., spaces left after the  line has been completed. It is paramount that tabs be used before a block and no spaces be left after a line.

Earlier, it was stated that all one has to do to execute a makefile is to run the make command with its arguments. However, this is not necessarily true. Running the make command will *only* execute the first target in a makefile, similar to running the makefile with a target name as the argument. To circumvent this, most make files have a target named all at the very beginning of the file, whose prerequisites are the list of targets which need to be executed as shown below.

```makefile
all: hello bye

hello:
	echo "Hello!"

bye:
	echo "Bye!"
```



### Targets

Targets make up the essence of makefiles.  They are the objects a makefile will act upon when running the commands they are comprised off. Targets are the names of files.
