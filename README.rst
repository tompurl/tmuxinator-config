======
README
======

My .tmuxinator Config
=====================

--------
Overview
--------

My tmuxinator_ config + a few handy aliases + my .tmux.config

Chances are, you don't want to use these files unless you're me :-)

You can see examples of my alias below in the Examples_ section.

-----
Setup
-----

Please note that the instructions below are for a machine that will use my
entire tmux setup. These steps should **not** be performed on a machine if 
you don't want to break you curren tmux or tmuxinator settings.

:: 

    # Install tmux using apt-get or whatever.
    # Install tmuxinator (https://github.com/aziz/tmuxinator)
    $ cd $HOME
    # Use the git read only url if you're not me.
    $ mv .tmuxinator .tmuxinator.bkup
    $ git clone git@github.com:tompurl/tmuxinator-config.git .tmuxinator
    $ ln -s $HOME/.tmuxinator/tmux.conf ~/.tmux.conf
    $ echo "source $HOME/.tmuxinator/aliases" >> ~/.bashrc
    $ echo "source $HOME/.tmuxinator/functions" >> ~/.bashrc
    $ source .bashrc # <= First time only

Examples
========

--------------------------
Attaching To A New Session
--------------------------

Let's say that you just started your computer and opened a terminal, and you
would like to start working on a Ruby script. Let's also assume that you
already have a profile file under ``~/.tmuxinator/`` called **rails-foo**. You
would start this "session" by typing the following command::

    $ sa rails-foo

-----------------------------------
Re-Attaching To An Existing Session
-----------------------------------

Now let's say that you want to check your system mail using ``mutt``. You know
that you have a Screen profile called **localhost** that has a ``mutt`` window,
so you decide to open it. 

Now, before you open a *new* Screen session using the **localhost** profile,
let's see if you are already have one running. Usually, it doesn't make sense
to open multiple Screen sessions using the same profile because it's confusing
and wastes resources. So let's see which Screen sessions are already running
on your machine::

    tom@flanders:~$ sls
    localhost: 3 windows (created Tue Jun  5 21:54:13 2012) [140x46]

What do you know? I already had a **localhost** session running. So let's
reattach to that::

    $ sr localhost

Ta-da! I'm now back in my old **locahost** Screen session. 

-----------------
Closing A Session
-----------------

Not yet implemented.

Commands
========

For more information, please see the ``functions`` and ``alises`` files.

    sa session_name
        Create a Screen session

    sls
        List all screen sessions

    sr [session_name]
        Reattach to an existing session. If you don't provide a session name,
        then you will attach to the first session listed using the ``sls``
        command.

    sk session_name
        Not yet implemented.

    si
        Not yet implemented.

    sd session_name
        Not yet implemented.

.. links

.. _tmuxinator: https://github.com/aziz/tmuxinator
