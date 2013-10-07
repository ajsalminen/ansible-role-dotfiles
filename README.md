ansible-role-dotfiles
=====================

Ansible role for pulling dotfiles to your home for per-app repositories a bit like tools such as Homesick.

# Usage

Clone the repo to the roles directory of you ansible playbook (I have it as roles/dotfiles). Create an inventory with something like this:

    [dev]
    localhost
    
Then create a playbook (or add to your other configuration):

    - hosts: dev 
      connection: local
      roles:
        - role: dotfiles
          home: /home/{{ansible_user_id}}
          dotfile_repos:
              - name: xmonad
                source: "{{home}}/projects/dotfiles/xmonad"
                version: HEAD
              - name: bash
                source: git://example.com/bash
                version: HEAD
     
Replacing the example repos with your own of course.
