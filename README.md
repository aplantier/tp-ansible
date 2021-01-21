# Tp-ansible

Compte Rendu de TP de Génie Locgiciel

Alexandre GUILLOT 
Theo DE PRATERE
Antoine PLANTIER


Creation de l'arborescence pour le tp : 

```bash 
$ > tree
.
├── inventory
│   ├── preprod
│   │   └── hosts
│   ├── prod
│   │   └── hosts
│   └── qualif
│       └── hosts
└── README.md

4 directories, 4 files

```

Configuration des hosts de ```inventory/qualif/hosts```

```bash
#fichier inventory/qualif/hosts

[sophiafront]
  front001.qualif.sophia.net
  front002.qualif.sophia.net
  front003.qualif.sophia.net

[bagnoletback]
  back001.qualif.bagnolet.net
  back002.qualif.bagnolet.net

[bagnoletdata]
  database001.qualif.bagnolet.net
  database002.qualif.bagnolet.net

[bagnoletvar]
  monitoring_server: monitoring.bagnolet.net
  
[sophia:children]
  sophiafront

[bagnolet:children]
  bagnoletback
  bagnoletdata
  bagnoletvar

[front:children]
  sophiafront

[back]

[database]

```

```bash
 ansible-playbook -i inventory/qualif playbook.yml -c local
 ____________
< PLAY [all] >
 ------------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||

 ________________________
< TASK [Gathering Facts] >
 ------------------------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||

[WARNING]: Platform linux on host database001.qualif.bagnolet.net is using the
discovered Python interpreter at /usr/bin/python2.7, but future installation of
another Python interpreter could change this. See https://docs.ansible.com/ansi
ble/2.9/reference_appendices/interpreter_discovery.html for more information.
ok: [database001.qualif.bagnolet.net]
[WARNING]: Platform linux on host back001.qualif.bagnolet.net is using the
discovered Python interpreter at /usr/bin/python2.7, but future installation of
another Python interpreter could change this. See https://docs.ansible.com/ansi
ble/2.9/reference_appendices/interpreter_discovery.html for more information.
ok: [back001.qualif.bagnolet.net]
[WARNING]: Platform linux on host front001.qualif.sophia.net is using the
discovered Python interpreter at /usr/bin/python2.7, but future installation of
another Python interpreter could change this. See https://docs.ansible.com/ansi
ble/2.9/reference_appendices/interpreter_discovery.html for more information.
ok: [front001.qualif.sophia.net]
[WARNING]: Platform linux on host back002.qualif.bagnolet.net is using the
discovered Python interpreter at /usr/bin/python2.7, but future installation of
another Python interpreter could change this. See https://docs.ansible.com/ansi
ble/2.9/reference_appendices/interpreter_discovery.html for more information.
ok: [back002.qualif.bagnolet.net]
[WARNING]: Platform linux on host database002.qualif.bagnolet.net is using the
discovered Python interpreter at /usr/bin/python2.7, but future installation of
another Python interpreter could change this. See https://docs.ansible.com/ansi
ble/2.9/reference_appendices/interpreter_discovery.html for more information.
ok: [database002.qualif.bagnolet.net]
[WARNING]: Platform linux on host front002.qualif.sophia.net is using the
discovered Python interpreter at /usr/bin/python2.7, but future installation of
another Python interpreter could change this. See https://docs.ansible.com/ansi
ble/2.9/reference_appendices/interpreter_discovery.html for more information.
ok: [front002.qualif.sophia.net]
[WARNING]: Platform linux on host database003.qualif.montsouris.net is using
the discovered Python interpreter at /usr/bin/python2.7, but future
installation of another Python interpreter could change this. See https://docs.
ansible.com/ansible/2.9/reference_appendices/interpreter_discovery.html for
more information.
ok: [database003.qualif.montsouris.net]
[WARNING]: Platform linux on host database004.qualif.montsouris.net is using
the discovered Python interpreter at /usr/bin/python2.7, but future
installation of another Python interpreter could change this. See https://docs.
ansible.com/ansible/2.9/reference_appendices/interpreter_discovery.html for
more information.
ok: [database004.qualif.montsouris.net]
[WARNING]: Platform linux on host front003.qualif.sophia.net is using the
discovered Python interpreter at /usr/bin/python2.7, but future installation of
another Python interpreter could change this. See https://docs.ansible.com/ansi
ble/2.9/reference_appendices/interpreter_discovery.html for more information.
ok: [front003.qualif.sophia.net]
 _____________________________________
< TASK [conf.server : Print the host] >
 -------------------------------------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||

ok: [back002.qualif.bagnolet.net] => {
    "changed": false,
    "msg": "Hostname back002.qualif.bagnolet.net"
}
ok: [back001.qualif.bagnolet.net] => {
    "changed": false,
    "msg": "Hostname back001.qualif.bagnolet.net"
}
ok: [database001.qualif.bagnolet.net] => {
    "changed": false,
    "msg": "Hostname database001.qualif.bagnolet.net"
}
ok: [database002.qualif.bagnolet.net] => {
    "changed": false,
    "msg": "Hostname database002.qualif.bagnolet.net"
}
ok: [front001.qualif.sophia.net] => {
    "changed": false,
    "msg": "Hostname front001.qualif.sophia.net"
}
ok: [front002.qualif.sophia.net] => {
    "changed": false,
    "msg": "Hostname front002.qualif.sophia.net"
}
ok: [front003.qualif.sophia.net] => {
    "changed": false,
    "msg": "Hostname front003.qualif.sophia.net"
}
ok: [database003.qualif.montsouris.net] => {
    "changed": false,
    "msg": "Hostname database003.qualif.montsouris.net"
}
ok: [database004.qualif.montsouris.net] => {
    "changed": false,
    "msg": "Hostname database004.qualif.montsouris.net"
}
 ____________
< PLAY RECAP >
 ------------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||

back001.qualif.bagnolet.net : ok=2    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
back002.qualif.bagnolet.net : ok=2    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
database001.qualif.bagnolet.net : ok=2    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
database002.qualif.bagnolet.net : ok=2    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
database003.qualif.montsouris.net : ok=2    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
database004.qualif.montsouris.net : ok=2    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
front001.qualif.sophia.net : ok=2    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
front002.qualif.sophia.net : ok=2    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
front003.qualif.sophia.net : ok=2    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   

```