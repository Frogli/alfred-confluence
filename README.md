![Alfred Confluence Workflow](https://github.com/skleinei/alfred-confluence/raw/master/design/banner.png)


# Alfred Confluence Workflow

Wouldn't it be nice to find and open Confluence pages – without opening a browser window and search in 
the Confluence web user interface?

The Alfred Confluence workflow is the solution: It makes the Confluence Quick search available from Alfred.
Just hit `⌘ Space` and type `c search term` to search for Confluence page.


## Getting Started

In order to get started:

1. Download the latest version of Alfred Confluence from the [Github releases page](https://github.com/skleinei/alfred-confluence/releases).
   * Click on the release you want to download.
   * Download the `alfred-confluence.alfred3workflow` file.
2. Double click to install Alfred Confluence in Alfred.
3. Configure Alfred Confluence with the following commands
   * `confluence_baseurl` - set the Confluence Base URL, e.g. 
     https://www.example.com/wiki or https://wiki.example.com
   * `confluence_username` - set your Confluence usename
   * `confluence_password` - set your Confluence password (it will be stored 
     securely in your MacOS keychain)
4. Use the `c` command to search your Confluence system. `c my search term`



## Advanced Configuration

If you work with multiple Confluence systems, Alfred Confluence supports this 
with config file.

In order to search multiple Confluence systems:

1. Create the file `~/.alfred-confluence.json` that contains a list of
   configuration for each system to be searchable. The first system will be
   treated as the _default_ system. 
   
   Example:
   
   ```[
     {
       "key": "wkc",
       "prefix": "[wkc] ",
       "baseUrl" : "https://www.k15t.com",
       "username" : "your-username",
       "password" : "your-unencrypted-password"
     },
     {
       "key": "cl",
       "prefix": "[Cloud] ",
       "baseUrl" : "https://k15t.jira.com/wiki",
       "username" : "your-username",
       "password" : "your-unencrypted-password"
     }
   ]
   ```
2. Use the following commands to search in the default
   * `c <search-query>` – search in the default system for pages `<search-query>`
   * `c <key> <search-query>` – search in the system with `<key>` for pages `<search-query>`

Please be aware that this will store you password in clear text on your file system.


## Feedback, Issues & Questions

Please raise any feedback issues and questions here: 
https://www.alfredforum.com/topic/10234-atlassian-confluence-quick-search/


## Development

### Building

To build Alfred Confluence just make:

```
$ make all
```

### Releasing

In order to release a new version:

1. Bump the version numbers (semantic version numbering!) in these files:
   * `src/Info.plist` (2 times: at the very end of the file AND line ~110 (for the workflow name))
   * `src/alfred-confluence.py` (line ~15)
2. Commit all changes.
3. Create a release on [Github](https://help.github.com/categories/releases/)
   and use the same version number.


## Credits

The Alfred Confluence workflow was build by Stefan Kleineikenscheidt 
([@skleinei](https://twitter.com/skleinei)). 

It was created in Python with the help of 
[Dean Jackson's](https://github.com/deanishe/alfred-workflow) Alfred library. 