
# sshchpwd.exp

Expect script to change login passwords using SSH

A few years ago I was supporting a very diverse environment with Solaris, AIX, and Linux servers; some with password logins, public/private key authentication, and several with SecurID passwords. All accounts were local, passwords expired every three months, and the accounts locked after three failed logins — so you can imagine the mess this created if you didn’t go around every server at least every three months. After I’d accumulated about half a dozen passwords, I wrote an Expect script to login and change my password and wrapped it with a bash script to try every old password I had. Since some servers needed a SecurID number to login, the bash script would pause on those and prompt me for the token before continuing. I’ve seen a few Expect scripts to change passwords, but none that can handle one-time tokens (like SecurID), expired passwords (changed before arriving at the prompt), and the variety of prompts to support Solaris, AIX, Linux, etc.

<pre><code>
# /usr/local/bin/sshchpwd.exp
#
# Expect script to change login passwords using SSH, with support for one-time
# tokens (like SecurID), expired passwords (changed before arriving at the
# prompt), on Solaris, AIX, Linux, etc.
#
# License: GPLv3
# License URI: http://www.gnu.org/licenses/gpl.txt
#
# Copyright 2012-2016 Jean-Sebastien Morisset (http://surniaulula.com/)
#
# Example:
#
#       $ export OLD_PASSWORD="oldpwd"
#       $ export NEW_PASSWORD="newpwd"
#       $ ./sshchpwd {server} {port} {token}
#
# The {port} and {token} command-line parameters are optional. If the server
# uses SecurID (or another one-time password), enter it on the command-line as
# the third parameter.
</code></pre>

