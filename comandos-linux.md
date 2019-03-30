comandos linux:
# en que directorio estoy?

        emontoya@hpcdis:~$ pwd
        /home/emontoya

# crear directorio datasets:

        emontoya@hpcdis:~$ mkdir datasets

# cambiar de directorio:

        emontoya@hpcdis:~$ cd datasets

# crear directorio 'papers-txt' y 'papers-pdf'

        emontoya@hpcdis:~/datasets1$ mkdir papers-txt
        emontoya@hpcdis:~/datasets1$ mkdir papers-pdf

# copiar muestra de archivos .txt y .pdf:

        emontoya@hpcdis:~/datasets1$ cp /opt/datasets/mcda-pi1-20191/papers-txt/0* papers-txt/
        emontoya@hpcdis:~/datasets1$ cp /opt/datasets/mcda-pi1-20191/papers-pdf/0* papers-pdf/

# listar archivos .txt:

        emontoya@hpcdis:~/datasets1$ cd papers-txt/
        emontoya@hpcdis:~/datasets1/papers-txt$ ls
        0704.3504.txt  0811.1254.txt  0903.1291.txt  0907.3965.txt  0911.1544.txt
        0706.1402.txt  0811.2853.txt  0903.2923.txt  0910.2912.txt  0911.1546.txt
        0710.0736.txt  0812.2709.txt  0903.4386.txt  0910.5577.txt  0911.2538.txt
        0803.2570.txt  0903.0197.txt  0904.2051.txt  0911.1507.txt  0911.2746.txt
        0808.0084.txt  0903.0199.txt  0907.3220.txt  0911.1509.txt  0911.5153.txt

# en que directorio estoy:

        emontoya@hpcdis:~/datasets1/papers-txt$ pwd
        /home/emontoya/datasets1/papers-txt
        emontoya@hpcdis:~/datasets1/papers-txt$