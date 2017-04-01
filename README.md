Users
=======

Setup users and groups on your system; optionally adding ssh keys and blocks to user's .profile

Create passwords using

```shell
python -c "from passlib.hash import sha512_crypt; import getpass; print (sha512_crypt.encrypt(getpass.getpass()))"
```

Role Variables
--------------

        users_groups:
          - name: sudo
            system: True
            gid: 5000
          - name: test

        users:
          - name: azmo
            fullname: Gordon Schulz
            groups: sudo
            uid: 1337
            password: '<pwd-hash>'
            expire_password: False
            home: /home/azmo
            shell: /bin/zsh
            profile: |
              alias gst='git status'
            ssh_keys:
              - 'ssh-rsa AAAAB3NzaC....'
              - 'ssh-rsa AAAADDSmsA....'


Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: azmodude.users }

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
