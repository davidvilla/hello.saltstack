Minimal ready-to-use [SaltStack](https://www.saltstack.com/) setup (master+minion) on a vagrant environment
    
    $ vagrant up
    $ vagrant ssh node1
    vagrant@node1:~$ sudo su
    root@node1:/home/vagrant# salt \* test.ping
    node1:
        True
    node2:
        True

    root@node1:/home/vagrant# salt \* state.highstate
