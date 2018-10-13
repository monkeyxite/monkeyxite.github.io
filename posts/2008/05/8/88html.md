<html><body><div>Using ipython in Mac OS X, finding that although the readline is already installed, but the autocompletion isn't available.Follow the instruction of this article, found that the configure file will disable the highlight.

So here is the improvement version of ~/.ipython/ipy_user_conf.py

P.S: Mac OS X v10.5.2; python 2.5.1; ipython 0.8.2

<code>
"""
uer configuration file for IPython
This is a more flexible and safe way to configure ipython than *rc files
(ipythonrc, ipythonrc-pysh etc.)
This file is always imported on ipython startup. You can import the
ipython extensions you need here (see IPython/Extensions directory).
Feel free to edit this file to customize your ipython experience.
Note that as such this file does nothing, for backwards compatibility.
Consult e.g. file 'ipy_profile_sh.py' for an example of the things
you can do here.
See http://ipython.scipy.org/moin/IpythonExtensionApi for detailed
description on what you could do here.

"""



# Most of your config files and extensions will probably start with this import
import IPython.ipapi
ip = IPython.ipapi.get()

# You probably want to uncomment this if you did %upgrade -nolegacy
# import ipy_defaults

def main():

# Handy tab-completers for %cd, %run, import etc.

# Try commenting this out if you have completion problems/slowness

# import ipy_stock_completers



# uncomment if you want to get ipython -p sh behaviour

# without having to use command line switches



# import ipy_profile_sh



import ipy_defaults

# o = ip.options

# An example on how to set options

#o.autocall = 1

# o.system_verbose = 0

#added to fix readline support, temporarily

import readline

readline.parse_and_bind ("bind ^I rl_complete")

main()

</code></div></body></html>