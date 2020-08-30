# hugo_asciidoc_ddd

This repository is just for testing gohugo  
- https://github.com/gohugoio/hugo/issues/5695
- https://github.com/gohugoio/hugo/pull/6561
- https://github.com/gohugoio/hugo/pull/7099

Here a Screenshot of

* Hugo
* Asciidoctor content
* usage of local Asciidoctor includes
* usage of asciidoctor-diagram 

![Screenshot](screenshot.png)

```
# to get theme
git submodule update --init --recursive
# optional: to use your own hugo build:
export PATH=$PATH:~/prototypes/hugo
# optional: to get hugo documentation modules
hugo mod get -u
```

Please check if parameters in `config.toml` are set correctly: 
```
[markup.asciidocext]
    args = ["--no-header-footer", "-r", "asciidoctor-html5s", "-b", "html5s", "-r", "asciidoctor-diagram"]
    workingFolderCurrent = true
```

Optional: Generate a PDF document (open issue: Hugo markup is rendered!):
```
# why has destination-dir a .. ? Answer: It is relative to base-dir
asciidoctor -v --trace \
      --require asciidoctor-pdf \
      --require asciidoctor-diagram \
      --backend pdf \
      --destination-dir ../build \
      --doctype book \
      --base-dir ./docs \
      -a imagesdir=images@ \
      ./docs/book-as-pdf.adoc
```

Run Hugo with parameter `--destination`:
```
hugo -v -d ./build server
```

This repo is tested on macOS and Windows with

* asciidoctor (2.0.10, 1.5.8)
* asciidoctor-diagram (2.0.2, 1.5.12)
* asciidoctor-html5s (0.5.0)
* graphviz (2.42.3)