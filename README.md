# blk

A simple bash script that makes it a breeze to block distracting websites.

## Features

* Block/unblock one or more websites at once, both via parameters and pipes.
* Block/unblock for a set period of time, for example *2 hours*.
* Block/unblock until a specific time, for example *13.38*.
* Unblock all blocked websites.
* List all blocked websites.

## Usage

### Block websites

    blk block <site1> <site2> <site3> ... [for <number> (seconds | minutes | hours | days) | until <time>]

### Unblock websites

    blk unblock <site1> <site2> <site3> ... [for <number> (seconds | minutes | hours | days) | until <time>]
    
### Unblock all blocked websites.

    blk unblock-all [for <number> (seconds | minutes | hours | days) | until <time>]

### List blocked websites

    blk list

### Examples

To block a website:

    blk block news.ycombinator.com

To block a couple of websites at once:

    blk block news.ycombinator.com www.facebook.com www.youtube.com

To unblock a website for 15 minutes:

    blk unblock news.ycombinator.com for 15 minutes

To block a website until 17.30:

    blk block news.ycombinator.com until 17.30
    
To block a list of websites, here defined in a file in the user's home directory:

    blk block $(cat ~/.block-list)
    or
    cat ~/.block-list | blk block

## Requirements

To use `blk` you need to have `bash` installed. I would recommend updating to the latest version if you haven't.

To block websites `blk` adds a line to the computer's hosts file that redirects the website to localhost. Depending on the permissions on your hosts file, you might need to run the script with `sudo`.

To use the `until` functionality you need to have the [`at`](http://manpages.ubuntu.com/manpages/xenial/en/man1/at.1.html) command installed and working. On macOS `at` is installed per default, but the `atrun` daemon is not running. To fix this, run `launchctl load -w /System/Library/LaunchDaemons/com.apple.atrun.plist` and restart your computer (see `man atrun` for more info).

## License

[MIT](LICENSE)
