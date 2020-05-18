---
title: Introduction to Jupyter Notebook
teaching: 30
exercises: 0
questions:
- "What is a Jupyter notebook and how does one access a notebook?"
- "How does one create a new notebook?"
- "How does one open an existing notebook?"
- "How does one execute programs using a notebook?"
objectives:
- "Navigate folders and files (the filesystem) using the Jupyter notebook interface."
- "Create and open files using the Jupyter notebook interface."
- "Distinguish Markdown and code cells."
- "Execute Python code snippets using the Jupyter notebook interface."
keypoints:
- Remember basic keyboard shortcuts.
- Distinguish command mode and edit mode.
---

## What is a Jupyter Notebook?

When one runs any program on a computer or a smartphone, one has to interact using an _interface_.  Most of the time, this just means the app menu (a table of icons), the Windows Start menu, or the like.  When one writes one's own code, however, the choice of how to execute that code is much broader.  We will use a _notebook_, which acts like a web page which lets you write and run code from within your browser.

When you run a Jupyter notebook, what you see is a web page with text, images, equations, videos, and executable code.  There are a few working parts that you need to get familiar with to use the notebook effectively, though.

<div class="alert alert-success">
The Jupyter team has provided a helpful <a href="http://jupyter-notebook.readthedocs.io/en/latest/examples/Notebook/Notebook%20Basics.html">introduction to working with notebooks</a>, including how to use the menu commands, toolbar, and keyboard shortcuts.
</div>


##  Getting Started

Depending on your machine, you may have several ways to access the Jupyter notebook server.  We assume that you have already [downloaded and installed Anaconda Python](https://www.anaconda.com/products/individual), which includes Jupyter notebook already.

1. Open the [Anaconda Navigator](https://docs.anaconda.com/anaconda/navigator/) by searching for it at the Start Menu or by double-clicking it on your Desktop.

    ![](https://docs.anaconda.com/_images/nav-defaults.png)

2. Open the Jupyter Notebook option (not JupyterLab, which is a related tool).  _After a moment, your browser should open with the Jupyter dashboard._

<div class="alert alert-warning">
If you do not have Anaconda Python installed, on macOS or Linux you should be able to access the Terminal and execute <code>jupyter notebook</code> to get started.  If you use this approach, be sure to keep the Terminal open the entire time you are working on the notebook.
</div>


## The Dashboard

When your browser opens to the Jupyter dashboard, you will see a listing of files and folders, presumably (but not always) your home directory.  The dashboard serves as a home page for Jupyter.  The tabs located across the tyop indicate the modes of access you have, and typically include `Files`, `Running`, and `Clusters`.  From `Files` you are able to access notebooks located in folders throughout your home folder.  From `Running` you can check on the status of active notebooks.


### Your First Notebook

We would like to start working on a new notebook, and for simplicity we will start one in a new folder.

1. Click the `New` button at top right.
2. Select the `Folder` option.
3. Name the folder `workshop` and confirm.

    _A new folder named `workshop` appears._

4. Click into the new folder, where we will create a new notebook.
5. Click the `New` button at top right.
6. Select the `Python 3` notebook option.

    _A new notebook starts in the current folder.  A new browser tab opens and shows you a clean-slate notebook._

The new notebook has a menu bar across the top and a toolbar for common actions.  The main thing that interests us is the cell, the gray bar which you can click in and type.

There are several kinds of cells, but the default cell is a _code cell_.

7. Click in the cell so that you see a cursor blinking.
8. Type `1+1` and press `Ctrl`+`Enter`.

    _The code you typed evaluates, produces the output `2`, and Jupyter inserts a new code cell below._

Your basic working pattern when using a notebook will be to enter code into a gray code cell, then execute the code using `Ctrl`+`Enter` (or the `Run` button on the toolbar).  You may then click back into the cell, edit the code, and run it again as necessary.

At this point, you can use the code cells like a calculator.  Try some of the following inputs in separate code cells:

-   `5 * 5`
-   `5 ** 2`  (what does this do?)
-   `25 ** 0.5`  (what does this do?)

The Python computing language, which we'll talk about in detail later, acts a lot like a graphing calculator for basic mathematical calculations.

Let's circle back around and talk a bit more about the Jupyter interface before diving into Python.

TODO

### `Files` Tab

The `Files` tab provides an interactive view of the portion of the filesystem which is accessible by the user.

The top of the files list displays clickable breadcrumbs of the current directory. It is possible to navigate the filesystem by clicking on these breadcrumbs or on the directories displayed in the notebook list.

To create a new folder, click the **`New`** dropdown button and select Folder. New folder will be named `Untitled Folder`. Check the checkbox of the folder and click `Rename` button to rename folder.

A new python notebook can be created by clicking on the **`New`** dropdown button at the top of the list, and selecting Python 3 kernel.

Notebooks can also be uploaded to the current directory by clicking the **`Upload`** button at the top of the list.

![files-tab](../pic/dashboard_notebooks_tab_5_0.png){:height="500px"}

### Running Tab

The running tab displays the currently running notebooks which are known to the server. This view provides a convenient way to track notebooks that have been started during a long running notebook server session.

Each running notebook will have an orange **`Shutdown`** button which can be used to shutdown its associated kernel. Closing the notebook's page is not sufficient to shutdown a kernel.

Running terminals are also listed, provided that the notebook server is running on an operating system which supports PTY(Unix, Linux, Mac, but not Windows).

When there are too many running notebooks, you could encounter "Too many open files" error and all open notebooks will stop working properly. You can either restart the Jupyter server or click "shutdown" buttons in Running tab to reduce number of open notebooks. Just closing the notebook page won't fix the issue.

![running-tab](../pic/dashboard_running_tab_4_0.png){:height="330px"}

## The Notebook

When a notebook is opened, a new browser tab will be created which presents the notebook user interface (UI). This UI allows for interactively editing and running the notebook document.  

A new notebook can be created from the dashboard by clicking on the Files tab, followed by the New dropdown button, and then selecting the language of choice(Python 3 for this course) for the notebook. From within a notebook, one can create a new python notebook by clicking **`File -> New Notebook -> Python 3`** from the notebook menu bar.

### Header

At the top of the notebook document is a header which contains the notebook title, a menubar, and toolbar. This header remains fixed at the top of the screen, even as the body of the notebook is scrolled. The menubar and toolbar contain a variety of actions which control notebook navigation and document structure.

When a new notebook is created, the title will be **Untitled**. By clicking the title, it can be edited in-place (which renames the notebook file).

![notebook-header](../pic/notebook_header_4_0.png){:height="100px"}

### Body

The body of a notebook is composed of cells. Each cell contains either markdown, code input, code output, or raw text. Cells can be included in any order and edited at-will, allowing for a large amount of flexibility for constructing a narrative. We will only be using **Code** and **Markdown** cells in this course.

- **Markdown cells** - These are used to build a nicely formatted narrative around the code in the document. The majority of this notebook is composed of markdown cells.

- **Code cells** - These are used to define the computational code in the document. They come in two forms: the *input cell* where the user types the code to be executed, and the *output cell* which is the representation of the executed code. Depending on the code, this representation may be a simple scalar value, or something more complex like a plot or an interactive widget.

![notebook-cells](../pic/notebook_cells.png){:height="150px"}

### Cell Mode

The notebook user interface is *modal*. This means that the keyboard behaves differently depending upon the current mode of the notebook. A notebook cell has two modes: **edit** and **command**.

**Edit mode** is indicated by a green cell border and a prompt showing in the editor area. When a cell is in edit mode, you can type into the cell, like a normal text editor.

![edit-mode](../pic/edit_mode.png){:height="70px"}

**Command mode** is indicated by a grey cell border. When in command mode, the structure of the notebook can be modified as a whole, but the text in individual cells cannot be changed. Most importantly, the keyboard is mapped to a set of shortcuts for efficiently performing notebook and cell actions. For example, pressing **`b`** when in command mode, will create a new cell below current cell.

![command-mode](../pic/command_mode.png){:height="70px"}


<br>
<div class="alert alert-success">
Enter edit mode by pressing `Enter` or using the mouse to click on a cell's editor area.
</div>
<div class="alert alert-success">
Enter command mode by pressing `Esc` or using the mouse to click *outside* a cell's editor area.
</div>
<div class="alert alert-warning">
Do not attempt to type into a cell when in command mode; unexpected things will happen!
</div>

## Basic Workflow
### Mouse Navigation

The first concept to understand in mouse-based navigation is that **cells can be selected by clicking on them.** The currently selected cell is indicated with a grey or green border depending on whether the notebook is in edit or command mode. Clicking inside a code cell's editor area or double clicking a command cell will enter edit mode. Clicking on the prompt or the output area of a cell will enter command mode.

The second concept to understand in mouse-based navigation is that **cell actions usually apply to the currently selected cell**. For example, to run a code cell, select it and then click the <button class='btn btn-default btn-xs'><i class="fa fa-play icon-play">| Run</i></button> button in the toolbar or the **`Cell -> Run`** menu item. Similarly, to change a code cell to markdown cell, click the drop down list in the tool bar and select Markdown or the **`Cell->Cell Type->Markdown`**. With this simple pattern, it should be possible to perform nearly every action with the mouse.

Markdown cells have one other state which can be modified with the mouse. These cells can either be rendered or unrendered. When they are rendered, a nice formatted representation of the cell's contents will be presented. When they are unrendered, the raw text source of the cell will be presented. To render the selected cell with the mouse, click the <button class='btn btn-default btn-xs'><i class="fa fa-play icon-play">| Run</i></button> button in the toolbar or the **`Cell -> Run`** menu item. To unrender the selected cell, double click on the cell.

### Keyboard Navigation

All actions in the notebook can be performed with the mouse, but keyboard shortcuts are also available for the most common ones. This is made possible by having two different sets of keyboard shortcuts: one set that is active in edit mode and another in command mode. Click <button class='btn btn-default btn-xs'><i class="fa fa-keyboard-o" aria-hidden="true"></i></button> button in the tool bar for all keyboard shortcuts. The essential shortcuts to remember are the following:

- **Esc**: Command mode
- **Enter**: Edit mode
- **Ctrl-Enter**: Run cell
- **Shift-Enter**: Run cell and go to next cell
- **Alt-Enter**: Run cell and insert a new code cell below
- **Under command mode**
  - **a**: Insert a new cell above
  - **b**: Insert a new cell below
  - **dd**: Delete cell. *Caution:cannot undo delete*
  - **y**: Change cell to Code cell
  - **m**: Change cell to Markdown cell

  ## Magics

  Jupyter provides specific commands, known as magics, that you can execute within a Code cell to provide enhanced functionality to the current notebook. Magics are not part of the Python programming language but can often make programming easier, especially within the notebook, and some magics can be used to improve your data processing work flow. Magics come in two types:

  1. line magics and
  2. cell magics.

  To see the list of currently available magics, execute the following cell.

`%lsmagic`
> ~~~
> Available line magics:
> %alias  %alias_magic  %autoawait  %autocall  %automagic  %autosave  %bookmark  %cat  %cd  %clear  %colors  %config  %connect_info  %cp  %debug  %dhist  %dirs  %doctest_mode  %ed  %edit  %env  %gui  %hist  %history  %killbgscripts  %ldir  %less  %lf  %lk  %ll  %load  %load_ext  %loadpy  %logoff  %logon  %logstart  %logstate  %logstop  %ls  %lsmagic  %lx  %macro  %magic  %man  %matplotlib  %mkdir  %more  %mv  %notebook  %page  %pastebin  %pdb  %pdef  %pdoc  %pfile  %pinfo  %pinfo2  %popd  %pprint  %precision  %prun  %psearch  %psource  %pushd  %pwd  %pycat  %pylab  %qtconsole  %quickref  %recall  %rehashx  %reload_ext  %rep  %rerun  %reset  %reset_selective  %rm  %rmdir  %run  %save  %sc  %set_env  %store  %sx  %system  %tb  %time  %timeit  %unalias  %unload_ext  %who  %who_ls  %whos  %xdel  %xmode
> Available cell magics:
> %%!  %%HTML  %%SVG  %%bash  %%capture  %%debug  %%file  %%html  %%javascript  %%js  %%latex  %%markdown  %%perl  %%prun  %%pypy  %%python  %%python2  %%python3  %%ruby  %%script  %%sh  %%svg  %%sx  %%system  %%time  %%timeit  %%writefile
Automagic is ON, % prefix IS NOT needed for line magics.
> ~~~
> {: .output}

### Line magic

A line magic is prepended by a single `%` character and will have any arguments specified all on the same line. Some useful line magics include:

- `%lsmagic`, which lists all currently defined line and cell magics for the current notebook,
- `%matplotlib`, which allows inline plotting to be enabled,
- `%autosave`, which sets the default autosave frequency in seconds, and
- `%timeit`, which in line mode times the execution of a single line of code.

### Cell magics

A cell magic is prepended by two `%` characters and they can have arguments that include both the current line and the remaining lines in the current cell. Thus, cell magics must be placed on the first line of a cell, and in general you can only have one cell magic per cell. Some useful line magics include:

- '%%timeit', which can be used to time a multi-line Python statement,
- '%%writefile' writes the contents of the cell into the named file,

If you are uncertain how to use a particular magic, you can always obtain help from the notebook kernel by entering the magic by itself in a cell, adding a `?` character at the end, and executing the cell to bring up the notebook help window.

## Writing Markdown Document

Markdown is a plain text formatting syntax that you can easily use to write text that can be converted to formatted text, for example, HTML. Markdown was developed by John Gruber, who runs the popular [Daring Fireball][df] blog.

You can view the source of a markdown cell by double clicking on it, or while the cell is selected in command mode, press Enter to edit it. Use Shift-Enter to re-render a markdown cell when it is in edit mode. We will introduce markdown in more details in next lesson.

## Writing and Executing Code

Of course, the reason we are using Jupyter Notebook is that it allows for in place development and execution of Python code. There are a number of direct benefits you accrue by developing and executing code in an Jupyter Notebook:

1. Run code in place with the output displayed in the notebook,  
2. Display visualizations inline,  
3. Run code in the background, while you edit or run code in other cells,  
4. Clean restarts of the notebook kernel, and  
5. Built-in support for parallelization.

The simplest of these capabilities to demonstrate is developing and running code in the notebook. The code can be a single line or multiple lines. Code cells can be executed by using one of three key combinations: CONTROL-return, which executes the cell in place, SHIFT-return, which executes the code and advances to the next cell, or ALT-return, which executes the code and insert a new code cell below. For example, as shown below, we have a single line of Python code that can be executed with the output directly shown.

> ~~~
>print("Hello World!")
> ~~~
> {: .language-python}
> ~~~
Hello World!
> ~~~
> {: .output}


Finally, to return to the dashboard, you can select the browser tab which contains it.  If you have closed the browser tab, you may access the dashboard from within a notebook by clicking the Jupyter icon at top left.
