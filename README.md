# blk

A simple bash script that makes it a breeze to block distracting websites.

## Installation

    brew tap mhgbrg/homebrew-tap
    brew install blk

To block websites `blk` adds a line to the computer's hosts file that redirects the website to localhost. Depending on the permissions on your hosts file, you might need to run the script with `sudo`. If you don't want to use `sudo`, you can change the permissions of the hosts file with `chmod 646 /etc/hosts` so that your user gets permission to write (this makes using the script **so** much more convenient).

Also make sure you have enabled the `atrun` daemon if you want to use automatic blocking/unblocking. See requirements for more info.

## Usage

To block a few websites:

    blk block news.ycombinator.com www.facebook.com www.youtube.com

Since this is the most common action, the `block` keyword can be omitted:

    blk news.ycombinator.com www.facebook.com www.youtube.com

To unblock:

    blk unblock news.ycombinator.com www.facebook.com www.youtube.com

You can also block/unblock for a limited time period:

    blk news.ycombinator.com for 2 hours

Or until a specific time:

    blk news.ycombinator.com until 21:00

To view all blocked and temporary unblocked websites, use the `list` command:

    blk list

To unblock all currently blocked websites, use the `unblock` command with the `all` parameter:

    blk unblock all

You can also block all websites in a predefined file by using the `block` command with the `all` parameter:

    blk block all

Or simply `blk all` (since `block` can be omitted). This command reads sites from the file `~/.blk-list`. If you want to use a different file, set the environment variable `BLK_LIST` to its path. For example, putting `export BLK_LIST=~/.distracting-websites.txt` in your `.bashrc` or `.zshrc` will make the above command use `~/.distracting-websites.txt`:

You can also feed sites to `blk` through stdin, for example:

    echo "news.ycombinator.com" | blk
    blk < ~/.distracting-websites.txt

## Requirements

To use `blk` you need to have `bash` installed. I would recommend updating to the latest version if you haven't.

To use the `for` and `until` functionality you need to have the [`at`](http://manpages.ubuntu.com/manpages/xenial/en/man1/at.1.html) command installed and working. On macOS `at` is installed per default, but the `atrun` daemon is not running. To fix this, run `launchctl load -w /System/Library/LaunchDaemons/com.apple.atrun.plist` and restart your computer (see `man atrun` for more info).

## License

[MIT](LICENSE)
