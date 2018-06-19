# F4-220
Some notes about the TerraMaster NAS F4-220

## Upgrading NodeJs and NPM
Install the GCC Utilities


Install the package for NodeJS that comes with TOS (node 5.8 and npm 3.7.3 in my case)


### Upgrade NPM (optional)
I tried to first upgrade npm to 4.3 (random version picked, the latest will not work), this step might be possible to skip.

`npm install -g npm@4.3`

If it complains about uid-number.js, edit the file and set `uidSupport = false` then try the install again.

### Install "n"
Next install "n" (https://www.npmjs.com/package/n)

`npm install -g n`

### Install `tar`
Because `n` uses `tar` with an option not available on BusyBox download and build a later version of the command.

``wget https://ftp.gnu.org/gnu/tar/tar-1.30.tar.gz --no-check-version

tar vfxz tar-1.30.tar.gz``

As a non-root user configure and make. Running configure as root will give a warning.

``cd tar-1.30

./configure

make``


I had to install as root though, due to not having write permission where it was installed.

`make install`

Then change the $PATH variable and make sure /usr/local/bin is listed before /bin.

`tar --version` should then output 1.30, if it does throw an error from BusyBox the path might not be correct.

### Install Node
`n 8.11.3`

If all is well, this should output a few lines and a success saying that node 8.11.3 is installed. 

Check with `node -v` the current version. 

Time to upgrade NPM to the latest (6.1.0 as of writing).

`npm install -g npm@latest`
