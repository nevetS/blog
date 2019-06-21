+++
title = "INIT Structure"
author = ["Steve Kallestad"]
lastmod = 2019-05-27T02:14:46-07:00
categories = ["emacs"]
draft = true
weight = 2002
+++

Over the years, my emacs initialization has gotten too complicated to manage in
a single file.  The problem I've found is that a singular file is too messy.
Turning off a feature is problematic.  Finding a setting in order to adjust it
is problematic.  And managing a sea of lisp is intimidating.

My .emacs.d path structure is as follows:

```shell
~/.emacs.d
├── auto-save-list # https://stackoverflow.com/questions/47985430/purpose-of-emacs-d-auto-save-list
├── autosaves      # automatically saved files.
├── backup         # backup files
├── configs        # lisp configuration of packages
├── elpa           # elpa/melpa packages get installed here
├── install        # an installation script to run
├── plugins        # packages/modules not installed via melpa (source)
└── init.el
```

There are two important paths as far as initialization goes, `configs` and
`plugins`.

Within init.el a list variable is declared (`sk:package-list`). Every package
on this list is loaded during initialization.  If it does not exist, it is
installed from one of the repositories (melpa, melpa-stable, or gnu).

Another list variable is declared (`sk:load-config-file`).  Every item in that
list represents a `.el` file within `configs/`.  Each of those files is loaded
in order.  (If a package is especially wieldly to configure, like org-mode,
it's configuration may be broken up into a subdirectory with categorized files).

If you want to change the way something behaves, inspect my configuration, or
adjust my configuration, simply take a look at the appropriate `.el` file.  For
example, to change the configuration for yasnippet, edit
`configs/yasnippet.el`.

Each configuration file, including `init.el` is pretty well commented.  You
don't have to be a lisp expert to understand them.

{{< highlight emacs-lisp "linenos=table, linenostart=1" >}}
;;; Package --- Steve's Emacs Initialization
;;
;;; Commentary:
;;     Steve's Emacs configuration, modularized to take the bite out of an
;;     entirely too large init.el
;;
;;     Packages are installed by configs/package.el, which is the first config
;;     file to be loaded.  If additional packages are desired, add the package
;;     name to the variable sk:package-list at the top of that configuration
;;     file.
;;
;;     There are many packages that are manually installed.  I tend to prefer
;;     manual installation over package installation because that allows for the
;;     privelege of installing updates prior to release of a package to one of
;;     the package repositories.  There are times when the package repositories
;;     are sorely out of date.
;;
;;     Each package installation consists of a config file in
;;     /configs/package-name.el and a similarly named directory in
;;     plugins/package-name that contains the plugin content.  Where possible
;;     the plugins/package-name directory is a git submodule pointed directly
;;     at the source repository of the official package.  Updating a package to
;;     the newest release should be a matter of 'git checkout tags/<release_name>'
;;     To view the installed release for a given submodule, the command
;;     'git branch' should respond with " *(Head detached at <release name>)"
;;; Code:



(defconst sk:emacs-config-dir (expand-file-name "configs/"
			      (file-name-directory load-file-name))
			      "Path to configuration and init files.")

(defconst sk:emacs-plugin-path (expand-file-name "plugins/"
			       (file-name-directory load-file-name))
			       "Path to plugins.")


;; utility function to auto-load my package configurations
(defun sk:load-config-file (filelist)
    "Iterate FILELIST and load each file."
    (dolist (file filelist)
      (load (expand-file-name
	     (concat sk:emacs-config-dir file)))
       (message "Loaded config file: %s" file)
       ))

(defvar sk:package-list)
;; these packages are installed by the package config file
(setq sk:package-list '(
			all-the-icons
			counsel ;
			counsel-projectile ;
			expand-region
			flycheck ; syntax checking for python
			jedi  ; jedi-mode for python development
			magit ; git integration
			web-beautify ; in order to use this, install
					; js-beautify with
					; npm -g install js-beautify
			yaml-mode ; yaml-mode
			highlight-parentheses ; highlight-parentheses-mode
			ivy ; ido-mode replacement
			ox-hugo ; org mode to Hugo exporter
			projectile ; projects in emacs
			rainbow-delimiters ; rainbow ([{
			scss-mode ; scss / sass css files
			spaceline ; mode line customizations
			spaceline-all-the-icons ; mode line update
			sqlup-mode ; make sql keywords uppercase
			company ; auto-completions with company mode
			hcl-mode ; hcl-mode for terraform
			htmlize ; org-export agenda
			flycheck-yamllint ; linting for yaml files via flycheck
			use-package ; tools for loading packages
			selected ; helper for multiple-cursors
			))


;; packages to be loaded configured are in alphabetical order except in the
;; following situations:
;; * package always comes first
;; * personal always comes last
;; * packages with dependencies are grouped together after the alphabetical list
(sk:load-config-file '(
		       "package"     ; installs any missing packages,
				     ; initializes packages
;; main packages
		       "autopair"    ;close parens/brackets/etc
		       "dockerfile-mode"      ;dockerfile-mode
		       "expand-region"
		       "erc"
		       "fci"         ;fill column indicator
		       "flycheck" ;multi=language linting
		       "flycheck-yamllint" ;linting for yaml
		       "graphviz"    ;graphviz mode
		       "gnus" ; gnus mail reader
		       "hcl-mode" ; hcl-mode configuration
		       "highlight-parentheses-mode"
		       "ivy" ; ido replacement
		       "ido"         ;ido directory and buffer completion - removed to try out ivy-mode
		       "js2-mode"    ;js2-mode for javascript development
		       "markdown-mode"    ;markdown mode
		       "multiple-cursors" ; multiple-cursors mode
;		       "org"         ;org-mode and custom org-mode configuration

		       "org/functions" ; functions specific to org-mode
		       "org/basics" ; basic org-mode configuration
		       "org/config_variables" ; org config variables
		       "org/agenda" ; org agenda
		       "org/babel" ; source code in org
		       "org/capture-templates" ; capture templates in org
		       "org/tasks" ; task configuration in org
		       "org/keybindings" ; keybindings in org
		       "org/appearance" ; org look and feel
		       "projectile"
		       "spaceline-all-the-icons" ; mode line update
		       "sqlup-mode" ; sqlup-mode configuration
		       "unbound"     ;find unbound keys
		       "window-number" ; window numbers
		       "yasnippet"   ;provides templated completions

;; python-mode.el and dependencies
		       "python-mode.el"
		       "dash" ; virtualenvwrapper dependency
		       "jedi" ; jedi-mode configuration
		       "rope" ; Pymacs and rope-mode, requires installation
			      ;  see emacs-init/install/pymacs-rope
		       "s" ; virtualenvwrapper dependency
		       "virtualenvwrapper"
;; personal settings

		       "labburn-theme" ;color-theme
		       "personal"

;; removed pacakges
		       ;; old configurations that are still here in case I want to re-enable them
		       ;; superseded in emacs24      "color-theme" ;change default color-scheme
		       ;; superseded in emacs22		       "linum"       ;line number mode
		       ))
(provide 'init)
;;; init.el ends here

{{< /highlight >}}
