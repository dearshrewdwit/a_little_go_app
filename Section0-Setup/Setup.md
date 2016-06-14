
# A Little Go App

## -1: Getting ready to Go

First things first. Clone [this repository][8]!

Then we need to [get Go][7].

Now follow the instructions! (the essentials are here below)

  - Create a workspace directory for your fab Go work. (`$HOME/go_workspace`)
  - Set the environment variable `GOPATH` to this fantastic directory.

The `GOPATH` environment variable specifies the location of your workspace. It is likely the only environment variable you'll need to set when developing Go code.

  - Your workspace can be located wherever you like! A common setup is to set `GOPATH=$HOME`.

Here it's set for the current shell session first and then for all future sessions in a specific directory:

```
$ export GOPATH=$HOME/your_go_workspace
$ echo "export GOPATH=$HOME/your_go_workspace" >> your_shell_profile
```

Next:
  - make the directories ` mkdir -p src/github.com/user/hello` inside your workspace (if you use GitHub, substitute your user name for user)
  - inside the hello directory create a file named `hello.go` with the contents in Section 0!


## 0: Hello world

Let's test the installation of Go to make sure everything is set up!

Look at this. This is some go:
```go
package main

import "fmt"

func   main() {
    fmt.Println(  "hello, world!"  );
    }
```
:)

Compile it with the go tool:
```
$ go install github.com/user/hello
```

Note that you can run this command from anywhere on your system. The go tool finds the source code by looking for the `github.com/user/hello` package inside the workspace specified by `GOPATH`.

The go tool will only print output when an error occurs, so if these commands produce no output they have executed successfully!!

The command above will put an executable command named `hello` inside the bin directory of your workspace. Execute the command to see the greeting:

```
$ $GOPATH/bin/hello
hello, world
```
By setting the `bin` directory in your path you can for convenience do the following:
```
$ export PATH=$PATH:$GOPATH/bin
$ hello
hello, world
```
AWESOME.
If you see "hello, world" then your Go installation is working.
If not. Well. Whoops! Time to debug :D

You should be able to understand every line of this program.
If you it's ok. Probably check out the [Go tour][1].

## Running your code


You can actually run the code in a couple of ways. From the directory containing `hello.go` run:

- `go run hello.go` compiles and runs only `hello.go`.

- `go build` compiles the code in the current directory and generates a binary named `hello` in the current directory.

- `go install` compiles the code in the current directory and generates a binary named `hello` in `$GOPATH/bin`.

Example folder structure:
```
    GOPATH=/home/user/gocode

    /home/user/gocode/
        src/
            foo/
                bar/               (go code in package bar)
                    x.go
                quux/              (go code in package main)
                    y.go
        bin/
            quux                   (installed command)
        pkg/
            linux_amd64/
                foo/
                    bar.a          (installed package object)
```

## Formatting your code: gofmt

If you're used to seeing some Go code you might have noticed that this code is not formatted in a standard way.

Try running `gofmt hello.go` and you'll see what the output should look like.
You can run `gofmt -d hello.go` to see how the file differs from the formatted version.
And finally you can run `gofmt -w hello.go` to simply rewrite the file with its formatted version.

## Managing import statements: goimports

The import statements at the beginning of the program are needed for the compiler to know what packages you use.
But this doesn't mean you need to write them yourself!

Try deleting the line `import "fmt"` from `hello.go` and run it, you should see an error:

```
    $ go run hello.go
    # command-line-arguments
    ./hello.go:5: undefined: fmt in fmt.Println
```

You can fix this error by manually adding the missing import statements or using `goimports`.

If you don't have `goimports` installed in your machine you can easily install it by running:

```
    $ go get golang.org/x/tools/cmd/goimports
```

This will install the `goimports` binary in `$GOAPTH/bin`.
It is basically the equivalent to fetching the code from GitHub and then running `go install`.

You can now run `goimports` as a replacement of `gofmt`.
`goimports` formats your code *and* fixes your imported package list adding missing ones and removing those unused.

Similarly to `gofmt` you can run:

- `goimports hello.go` to see what the fixed file would look like.
- `goimports -d hello.go` to see the difference between the current and fixed versions.
- `goimports -w hello.go` to rewrite the file with its fixed version.

## Making your life easier

`gofmt` and `goimports` are just two of the tools that you might use to make your life easier.
To have those and more invoked everytime you save your file you should consider adding a plugin to your favorite editor.
Some folk love [vim][2] with [vim-go][3], some also use [VS Code][4] with its Go plugin.
But there are many more editors with Go support, you can find them [here][5].

# Congratulations!

You're done with ... set up. Well, we need to start somewhere!
But hey, at least now you're ready to tackle [section 1][6].

[1]: https://tour.golang.org
[2]: http://www.vim.org/
[3]: https://github.com/fatih/vim-go
[4]: https://www.visualstudio.com/en-us/products/code-vs.aspx
[5]: https://github.com/golang/go/wiki/IDEsAndTextEditorPlugins
[6]: ../section01/README.md
[7]: https://golang.org/doc/code.html
[8]: https://github.com/dearshrewdwit/a_little_go_app
