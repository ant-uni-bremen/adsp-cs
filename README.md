[![License: CC BY-SA 4.0](https://img.shields.io/github/license/ant-uni-bremen/adsp-cs)](https://img.shields.io/github/license/ant-uni-bremen/adsp-cs)

# Introduction
The jupyter notebook `basic_reconstruction.ipynb` is used in the lecture to show some examples and illustrations about compressed sensing reconstruction.

## Jupyter requirements
Make sure that you have jupyter installed with nodejs (conda example)
```
conda install nodejs
```
or (Ubuntu/Debian example)
```
sudo apt install nodejs
```

The interactive figures are based on [IPythonWidgets](https://ipywidgets.readthedocs.io/en/latest/user_install.html) and [IPympl](https://github.com/matplotlib/ipympl)
```
pip install ipywidgets
pip install ipympl
```

## CS packages
Furthermore, you need to install [primal](https://github.com/ShenQianli/primal), [fastmat](https://github.com/EMS-TU-Ilmenau/fastmat), and [vympyre](https://github.com/GAMPTeam/vampyre)

These are not available via PyPI packages (at least using the latest version) and can only be installed by cloning the repository. So for example like this:
```
mkdir git
cd git

git clone https://github.com/GAMPTeam/vampyre.git
cd vampyre; pip install . 

cd ..
git clone https://github.com/EMS-TU-Ilmenau/fastmat.git
cd fastmat; pip install .

cd ..
git clone --recurse-submodules https://github.com/ShenQianli/primal.git
cd primal; make Pyinstall
```
In my case primal failed due to the fact that Ubuntu names the Python binary `python3` even if no Python 2.X version is installed. Just edit the following part of the `Makefile`

```
# install python-package
Pyinstall: ${PSM_DYLIB}
	rm -rf python-package/pyprimal/lib/
	mkdir python-package/pyprimal/lib/
	cp -rf ${PSM_DYLIB} python-package/pyprimal/lib/
	cd python-package; python setup.py install; cd ..
```
By changing `python` in the last line to `python3`
