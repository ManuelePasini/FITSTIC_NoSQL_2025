# Introduzione al Terminale in Unix/Linux

Il terminale è un'interfaccia a riga di comando (CLI) che permette di interagire con il sistema operativo eseguendo comandi testuali. È uno strumento potente utilizzato per gestire file, processi e configurazioni di sistema in modo efficiente.

## Comandi di Base

### 1. Navigazione nel File System

```bash
pwd  # Mostra il percorso della directory corrente
ls   # Elenca i file e le directory nella directory corrente
cd [directory]  # Cambia directory
cd ..  # Torna alla directory superiore
```

### 2. Gestione di File e Directory

```bash
touch [file]  # Crea un nuovo file vuoto
mkdir [directory]  # Crea una nuova directory
rm [file]  # Rimuove un file
rm -r [directory]  # Rimuove una directory e il suo contenuto
cp [sorgente] [destinazione]  # Copia file o directory
mv [sorgente] [destinazione]  # Sposta o rinomina file o directory
```

### 3. Visualizzazione e Modifica di File

```bash
cat [file]  # Visualizza il contenuto di un file
less [file]  # Visualizza il contenuto di un file con navigazione interattiva
nano [file]  # Editor di testo semplice
vim [file]  # Editor di testo avanzato
```

### 4. Gestione dei Processi

```bash
ps  # Mostra i processi attivi
top  # Mostra i processi in tempo reale
kill [PID]  # Termina un processo specifico
killall [nome-processo]  # Termina tutti i processi con un determinato nome
```

## Gestione dei Permessi in Unix/Linux

In Unix/Linux, i permessi definiscono chi può leggere, scrivere o eseguire file e directory. Ogni file ha tre categorie di permessi:

- **Utente (Owner)**: il proprietario del file
- **Gruppo (Group)**: gli utenti appartenenti al gruppo del file
- **Altri (Others)**: tutti gli altri utenti

I permessi sono rappresentati con tre lettere:

- **r** (read) - Permette di leggere il file
- **w** (write) - Permette di scrivere/modificare il file
- **x** (execute) - Permette di eseguire il file

### 1. Visualizzazione dei Permessi

```bash
ls -l  # Mostra i dettagli dei file, inclusi i permessi
```

Esempio di output:

```
-rw-r--r-- 1 user user 1234 Mar 6 10:00 file.txt
```

- Il primo carattere indica il tipo di file (`-` per file, `d` per directory).
- I caratteri successivi indicano i permessi per utente, gruppo e altri utenti.

### 2. Modifica dei Permessi

```bash
chmod [permessi] [file]  # Cambia i permessi di un file
chown [utente]:[gruppo] [file]  # Cambia il proprietario di un file
chgrp [gruppo] [file]  # Cambia il gruppo di un file
```

Esempio:

```bash
chmod 755 script.sh  # Imposta i permessi a rwxr-xr-x
chown user:group file.txt  # Cambia proprietario e gruppo
chgrp developers file.txt  # Cambia il gruppo di un file
```

## Aiuto e Documentazione

Per ottenere informazioni dettagliate su un comando, si possono usare:

```bash
[comando] --help  # Mostra un riepilogo delle opzioni disponibili
man [comando]  # Mostra la documentazione completa del comando
```

Esempio:

```bash
ls --help  # Mostra le opzioni disponibili per 'ls'
man ls  # Mostra il manuale di 'ls'
```
