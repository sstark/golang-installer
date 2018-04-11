
golang-installer
================

Little helper script for zsh that I use to keep my go installations organized. Assumes
there is a directory /usr/local/go that is writable by your own user account.

    > golang-installer 
    go versions installed in /usr/local/go:
    1.8.2 1.8.3 1.8.4 1.8.5 1.9.1 1.9.2
    > golang-installer 1.10
    getting https://storage.googleapis.com/golang/go1.10.linux-amd64.tar.gz...
    unpacking /tmp/tmp.xyKoQgvUxE into /usr/local/go/1.10...
    > golang-installer     
    go versions installed in /usr/local/go:
    1.8.2 1.8.3 1.8.4 1.8.5 1.9.1 1.9.2 1.10

Handy function to use along with this:

    find_go_path () {
        # place in .zshenv and append output to $path
        local go_paths latest_version
        go_paths=(/usr/local/go/*/bin(N))
        if [[ $#go_paths -gt 0 ]]
        then
            latest_version=${${(On)go_paths}[1]}
            print $latest_version
        else
            print /usr/local/go/bin
        fi
    }

This will automatically use the most recent go version found.
