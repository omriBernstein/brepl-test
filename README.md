If you are looking to try out [ClojureScript](https://github.com/clojure/clojurescript) online, this is not that. Instead, [see here](http://clojurescript.net/). Below are instructions for getting a local ClojureScript browser [REPL](http://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) up and running, based eniterly on [this video](http://www.youtube.com/watch?v=OqCOA8P8QOY&noredirect=1). You will need:
<br>&nbsp;&nbsp;0. A [computer](http://www.urbandictionary.com/define.php?term=computer)
<br>&nbsp;&nbsp;1. The digital folder and files that go with this README
<br>&nbsp;&nbsp;2. A [command line interace](http://en.wikipedia.org/wiki/Command-line_interface) program for your operating system, also known as a "terminal"
<br>&nbsp;&nbsp;3. An [internet browser](http://en.wikipedia.org/wiki/Web_browser)
<br>&nbsp;&nbsp;4. [Leiningen](http://leiningen.org/) version 2.0.0 or higher

##Get started

This README goes with a folder. Make sure you've downloaded this folder first. Open a terminal and navigate to the directory this file is in. For me, the command to get there is:

    cd /home/Omnomnomri/Documents/Codescratch/brepl-test

For you, it will be `cd` followed by a space and then the path to that folder. With leiningen version 2.0.0 or higher installed, now enter into the terminal:

    lein cljsbuild once

Wait for the project to compile, giving the following output before returning once more to an input field:

    Compiling ClojureScript.
    Compiling "brepl-test.js" from ["src"]...
    Successfully compiled "brepl-test.js" in 14.901984032 seconds.

##Run the REPL

Now enter (still in the proper directory):

    rlwrap -pBLUE lein trampoline cljsbuild repl-listen

Wait for the following to appear in the terminal:

    Running ClojureScript REPL, listening on port 9000.
    "Type: " :cljs/quit " to quit"
    ClojureScript:cljs.user>

This last line should be an input prompt, where you can type commands to the REPL, but don't do that yet. First, in an internet browser, go to:

    localhost:9000/brepl-test.html

Now go back to the terminal and try out the REPL.

##Examples

Any calls to JavaScript will affect the open browser window, for example:

    (js/alert "Finally robotic beings rule the world.")

The REPL should give `nil` output, and in the internet browser window, you should see a JavaScript alert pop up. Or functions without a JavaScript side-effect will simply return their value in the REPL. Such as:

    (map :human-status [{:name "Remaining human 1/2" :human-status "dead"} {:name "Remaining human 2/2" :human-status "dead"}])

Which should return:

    ("dead" "dead")

When you want to quit the REPL, type in:

    :cljs/quit

##Recurring use

If you want to run this local browser REPL again, just follow the instructions starting at [**Run the REPL**](#run-the-repl). If, as it has for me, the REPL sometimes becomes unresponsive&#8212;neither working nor explicitly erroring&#8212;try doing `lein cljsbuild once` again and retry.
