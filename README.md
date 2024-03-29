# TWEPP_2021_Paper

TWEPP 2021 conference proceedings.

TWEPP 2021 Links
- [Overview](https://indico.cern.ch/event/1019078/)
- [Proceedings instruction for authors](https://indico.cern.ch/event/1019078/page/22920-proceedings-instruction-for-authors)
- [Poster contribution](https://indico.cern.ch/event/1019078/contributions/4444260/)
- [JINST instruction for authors](https://jinst.sissa.it/jinst/help/helpLoader.jsp?pgType=author)

To compile on macOS (runs pdflatex and bibtex commands using Makefile):
```
cd latex
make
```

## Instructions to make tarball

Instructions for creating a tarball to upload the paper (e.g. for JINST, arXiv, ...).
First, create directories to use for the tarball and copy the necessary files.
In this example, we use the name "jinst-v1".
```
mkdir -p tarballs
cd tarballs
mkdir jinst-v1
cd jinst-v1
rsync -az ../../latex/ .
rsync -az ../../figures .
```

Edit this new copy of twepp_paper.tex: Change "../figures" to "figures" throughout file.

Check that Latex compiles and outputs the expected PDF:
```
make clean
make
show twepp_paper.pdf
```

Create tarball:
```
tar -czvf jinst-v1.tar.gz *
mv jinst-v1.tar.gz ..
cd ..
```

Check that tarball works:
```
mkdir tmp
cp jinst-v1.tar.gz tmp
cd tmp
tar -zxvf jinst-v1.tar.gz
```

Compile and check pdf:
```
make clean
make
show twepp_paper.pdf
```

Remove directory:
```
cd ..
rm -r tmp
```
