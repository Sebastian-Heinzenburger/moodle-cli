# moodle-cli

moodle-cli is the result of reverse engineering my
schools moodle platform and studying the moodle 
[source code](https://git.moodle.org/gw?p=moodle.git;a=summary).
moodle-cli aims to provide the means for automating
certain actions and making it easier to gather information
all from the command line.

## Examples

```shell
$ msession
a01bcdef23g4567hij8klm9nop

$ mid "Jonathan"
603;Brooks Jonathan
1760;Banks Jonathan

$ muser 1760
1760: Banks Jonathan

$ mmail $(mid "Jonathan Banks" -s)
1760: jonathan.banks@gmx.com

$ mcourses $(mid "anks" -s)
1760:
Schueler:1760;
Kurs-ID: 1406;
Fach: REV;
Klasse: JS1;
Lehrer: Apel;
Jahr: Abitur 2023

Schueler:1760;
Kurs-ID: 1456;
Fach: Gk1;
Klasse: JS1;
Lehrer: Jennings;
Jahr: Abitur 2023

Schueler:1760;
Kurs-ID: 1529;
Fach: G;
Klasse: JS1;
Lehrer: Moller;
Jahr: Abi2023

Schueler:1760;
Kurs-ID: 1798;
Fach: Wi;
Klasse: JS1;
Lehrer: Rivera;
Jahr: Abi2023
...

$ mdetails 1760 1406
1760: jonathan.banks@gmx.com;Harrisburg -  Pennsylvania 
```

### Automation

This command lists all email addresses of contacts containing
"anna" in their name (if stated and set to public/visible for course members).
```shell
$ mid "anna" | awk -F";" '{ print $1 }' | xargs -L1 mmail
543:
713: anna.johns@icloud.com
765:
806:
828: sanna.Hart@gmail.de
887:
950:
1026:
1105: annadean32@gmx.com
1101:
1244:
1293: Johanna-Obrien@gmx.net
1437:
1457:
1510:
1735:
1773:
```

