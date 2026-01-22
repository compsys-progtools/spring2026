# Other Course Software/tools


## Courseutils

This is how your badge issues are created. It also has some other utilities for the course. It is open source and questions/issues should be posted to its [issue tracker](https://github.com/compsys-progtools/courseutils/issues)


## Jupyterbook 


### Changing paths on windows
To edit a path on windows, go to the search bar and type 'edit environment variables', click the environment variable button, click on 'path' then new, then insert the new path

### Avoiding windows security block
The closest thing to work around the security block is to exclude files, to exclude a file, take note of the file and know where to find it, go to windows security, virus protection and threat protection, scroll down to exclusions, add or exclude folders, then add the specific folder that is getting blocked


## How to get a bibtex From google Scholar


To use a source from google scholar in a jupyter book or this site
1. find your source, check that you have the one coming from an official venue, not Arxiv if possible
1. click "cite" below the source
1. click "BibTeX" at the bottom of the popup
1. copy that value and put it in a `.bib` file


Here is what one citation might look like
```{code-block} bibtex
:filename: references.bib
:label: bibexample
@article{geiger2018types,
  title={The types, roles, and practices of documentation in data analytics open source software libraries: a collaborative ethnography of documentation work},
  author={Geiger, R Stuart and Varoquaux, Nelle and Mazel-Cabasse, Charlotte and Holdgraf, Chris},
  journal={Computer Supported Cooperative Work (CSCW)},
  volume={27},
  number={3},
  pages={767--802},
  year={2018},
  publisher={Springer}
}
```
on this site I can then use `@geiger2018types` to cite the source. So, for example: 

:::::{tab-set}
:::{tab} Myst Markdown
```Markdown
In data science, developers think they should spend more time than they do on documentation @geiger2018types.  
```
:::
:::{tab} Rendered
In data science, developers think they should spend more time than they do on documentation @geiger2018types. 
:::
::::::: 

In jupyter book you can use the `cite` directive for similar output

In data science, developers think they should spend more time than they do on documentation {cite}geiger2018types.  
