# Changelog

This extended repository tracks the master branch [sphinx-book-theme] (https://github.com/executablebooks/sphinx-book-theme).  The most recent commit of the master incorporated is [8822eef](https://github.com/executablebooks/sphinx-book-theme/commit/8822eeff673f14e627925a51070d5eeaf3360dbe)

## The following files have been added:

* `src/sphinx_book_theme/theme/sphinx_book_theme/static/images/Logo_revealjs.png`
* `src/sphinx_book_theme/theme/sphinx_book_theme/static/images/PowerPoint.svg`
* `src/sphinx_book_theme/theme/sphinx_book_theme/static/images/logo_jupyterdeck.svg`
* `src/sphinx_book_theme/theme/sphinx_book_theme/static/images/logo_jupyterlite.svg`
* `src/sphinx_book_theme/theme/sphinx_book_theme/static/images/logo_lightning_studio.svg`

## The following code extensions have been made:

### in file `src/sphinx_book_theme/header_buttons/launch.py`

at line 52:
``` diff
-         for key in ("binderhub_url", "jupyterhub_url", "thebe", "colab_url")
+         for key in ("binderhub_url", "jupyterhub_url", "thebe", "colab_url", "use_lite_button", "use_reveal_button", "use_powerpoint_button", "use_deck_button")
```   

at line 119:
``` diff   
+  lightning_studio_url = launch_buttons.get("lightning_studio_url", "").strip("/")
```   

at lines 192-206:
``` diff     
+ 		if lightning_studio_url:
+ 			if provider.lower() != "github":
+ 				SPHINX_LOGGER.warning(f"Provider {provider} not supported on Lightning.")
+ 			else:
+ 				github_path = f"%2F{org}%2F{repo}%2Fblob%2F{branch}%2F{path_rel_repo}"
+ 				url = f"{lightning_studio_url}/new?repo_url=https://github.com{github_path}"
+ 				launch_buttons_list.append(
+ 					{
+ 						"type": "link",
+ 						"text": "Lightning Studio",
+ 						"tooltip": translation("Launch on") + " Lightning Studio",
+ 						"icon": "_static/images/logo_lightning_studio.svg",
+ 						"url": url,
+ 					}
+ 				)
```   

at lines 220-270:
``` diff  			
+ 		path_rel_repoB = path_rel_repo[path_rel_repo.index("/") + 1:]
+ 
+ 		if launch_buttons.get("use_lite_button", False):
+ 			url = f"./Lite/lab?path={path_rel_repoB}"
+ 			launch_buttons_list.append(
+ 				{
+ 					"type": "link",
+ 					"text": "JupyterLite",
+ 					"tooltip": translation("Launch on") + " JupyterLite",
+ 					"icon": "_static/images/logo_jupyterlite.svg",
+ 					"url": url,
+ 				}
+ 			)
+ 
+ 		if launch_buttons.get("use_reveal_button", False):
+ 			url = f"./slides/{path_rel_repoB}"[:-5] + "slides.html"
+ 			launch_buttons_list.append(
+ 				{
+ 					"type": "link",
+ 					"text": "Reveal.js",
+ 					"tooltip": translation("Launch on") + " Reveal.js",
+ 					"icon": "_static/images/Logo_revealjs.png",
+ 					"url": url,
+ 				}
+ 			)
+ 
+ 		if launch_buttons.get("use_powerpoint_button", False):
+ 			url = f"./PowerPoint/{path_rel_repoB}"[:-5] + "pptx"
+ 			launch_buttons_list.append(
+ 				{
+ 					"type": "link",
+ 					"text": "PowerPoint",
+ 					"tooltip": translation("Launch on") + " PowerPoint",
+ 					"icon": "_static/images/PowerPoint.svg",
+ 					"url": url,
+ 				}
+ 			)
+ 
+ 		if launch_buttons.get("use_deck_button", False):
+ 			url = f"./Deck/lab?path={path_rel_repoB}"
+ 			launch_buttons_list.append(
+ 				{
+ 					"type": "link",
+ 					"text": "JupyterDeck",
+ 					"tooltip": translation("Launch on") + " JupyterDeck",
+ 					"icon": "_static/images/logo_jupyterdeck.svg",
+ 					"url": url,
+ 				}
+ 			)
```   
  