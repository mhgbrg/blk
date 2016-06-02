# block

A simple bash scripts that makes it a breeze to block distracting websites.

## Usage

The default behaviour of block is to block a website. The website to block can either be specified with the `-s` flag, or by piping output from another script. When piping, the script expects one website per line.

block also has support for blocking and unblocking websites for only a set time period with the `-t` flag. This is an optional flag, and if not specified the website will stay blocked or unblocked until further action.

### Examples

To block a website:

    block -s news.ycombinator.com

To unblock a website:

    block -u -s news.ycombinator.com

To block a list of websites, here defined in a file in the users home folder:

    cat ~/.block-list | block

To unblock a website for 15 minutes:

    block -u -s news.ycombinator.com -t 15

To list all blocked websites:

    block -l

## How it works

The inner workings of block is ridiculously simple. To block websites it adds a line to the computer's hosts file that redirects the website to localhost.
