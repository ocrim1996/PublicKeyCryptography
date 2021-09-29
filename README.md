# PublicKeyCryptography

Una volta eseguito il codice, l’utente può scegliere tra una lista di funzioni disponibili che vengono stampate a schermo, semplicemente inserendo il numero corrispondente.

![Schermata 2021-05-03 alle 15.51.44.png](https://res.craft.do/user/full/63cec524-c1b6-57b4-8157-df0476f848cb/doc/38F3E494-D23E-4204-B3AC-F14F8DF5026D/711956AF-2EF8-4EB9-B303-82055EBBD124_2)

Mostriamo dunque adesso una breve descrizione delle seguenti funzioni e cosa richiedono in input.

## 1. Algoritmo di Euclide Esteso (Extended Euclidean Algorithm)

La funzione prende in ingresso due numeri interi e restituisce l’***MCD*** (**Massimo Comun Divisore**) e i coefficienti dell’**identità di Bezout** ***(x,y)***.

In particolare in termini matematici:

![equation](https://latex.codecogs.com/gif.latex?%5Ctext%7BDati%202%20interi%20%7D%20a%20%5Ctext%7B%20e%20%7D%20b%20%5Ctext%7B%20l%27algoritmo%20di%20Euclide%20esteso%20restituisce%203%20interi%20%7D%20d%2Cx%20%5Ctext%7B%20e%20%7D%20y%20%5Ctext%7B%20tali%20che%3A%7D%5C%5C%20d%20%3D%20a%20%5Ccdot%20x%20&plus;%20b%20%5Ccdot%20y%5C%5C%20%5Ctext%7Bdove%3A%7D%5C%5C%20%5Cbullet%20%5Cquad%20d%20%5Crightarrow%20%5Ctext%7B%20il%20massimo%20comun%20divisore%20tra%20a%20e%20b.%7D%5C%5C%20%5Cbullet%20%5Cquad%20a%2Cb%20%5Crightarrow%20%5Ctext%7Bsono%20i%20coefficienti%20dell%27identita%27%20di%20Bezout.%7D)

Nel codice la funzione che calcola l’algoritmo di Euclide esteso è:

```python
def extended_euclidean(a, b):
	'''some code'''
	return d,x,y
```

Mentre la funzione che imposta i valori dei parametri in input è:

```python
def set_extended_euclidean():
	'''some code'''
```

## 2. Algoritmo di esponenziazione modulare veloce (Fast Modular Exponentiation)

L’algoritmo di esponenziazione modulare veloce permette di calcolare in maniera efficiente operazioni del tipo:

![equation](https://latex.codecogs.com/gif.latex?d%20%3D%20a%5E%7Bexp%7D%5C%2Cmod%5C%2Cn)

dove in applicazioni reali come l’*encryption* e *decryption* di RSA, i valori di **a**,**exp** e **n** possono essere molto grandi (dell’ordine di almeno 10^100).

All’utente dunque viene richiesto di inserire in input 3 numeri interi:

- **`a`** → la base.
- **`exp`** → l’esponente.
- **`n`** → il modulo.

E l’algoritmo da in output il valore dell’esponenziazione veloce **d**.

Nel codice la funzione che esegue l’algoritmo di esponenziazione modulare veloce è:

```python
def fast_modular_exponentiation(a, exp, n):
	'''some code'''
	return d
```

Mentre la funzione che imposta i valori dei parametri in input è:

```python
def set_fast_modular_exponentiation():
	'''some code'''
```

La correttezza di tale algoritmo segue da due invarianti soddisfatte:

![equation](https://latex.codecogs.com/gif.latex?%5Cbullet%20%5Cquad%20%5Ctext%7BAl%20termine%20di%20ogni%20iterazione%20del%20ciclo%20for%2C%20vale%20%7D%20d%20%3D%20a%5E%7Bc%7D%5C%2Cmod%5C%2Cn.%5C%5C%20%5Cbullet%20%5Cquad%20%5Ctext%7BAl%20termine%20dell%27ultima%20iterazione%20del%20ciclo%20for%2C%20vale%20%7D%20c%20%3D%20exp.)

Dove la variabile **d** accumula i prodotti parziali, mentre la variabile **c** è un contatore, che rappresenta il valore dell’esponente al termine dell’*i*-esima iterazione.

## 3. Test di Miller-Rabin

Il test di Miller-Rabin viene utilizzato per stabilire se un numero dato in input è un numero *composto* o un numero *primo*.

In particolare l’utente deve inserire un numero intero su cui effettuare il test e un numero massimo di ***rounds*** da far eseguire all’algoritmo. Se il numero inserito risulta composto la funzione ritorna il valore *True* altrimenti se è un numero primo la funzione ritorna il valore *False*.

Si può osservare che più il numero di rounds è alto e più il test è accurato per la risposta False,  ma è anche più oneroso in termini computazionali. Una giusta via di mezzo si ha per ***rounds = 40*** (che viene anche consigliato di default). Comunque l’utente come precedentemente detto può scegliere arbitrariamente tale valore.

Nel codice la funzione che esegue il test di Miller-Rabin è:

```python
def miller_rabin_test(n, rounds=40):
	'''some code'''
	return True/False
```

Mentre la funzione che imposta i valori dei parametri in input è:

```python
def set_miller_rabin_test():
	'''some code'''
```

In termini matematici il **test di Rabin** può essere definito come segue:

![equation](https://latex.codecogs.com/gif.latex?comp_%7BR%7D%28x%2Cn%29%20%3D%20vero%20%5Ciff%200%20%3C%20x%20%3C%20n%20%5Ctext%7B%20e%2C%20posto%20%7D%20n-1%20%3D%202%5E%7Br%7Dm%2C%20%5Ctext%7B%20con%20%7D%20m%20%5Ctext%7B%20dispari%2C%20nella%20sequenza%7D%5C%5C%20x_%7B0%7D%20%3D%20x%5E%7Bm%7D%5C%2Cmod%5C%2Cn%5C%5C%20x_%7B1%7D%20%3D%20x_%7B0%7D%5E%7B2%7D%5C%2Cmod%5C%2Cn%20%5Cquad%20%28%5Cequiv_%7Bn%7Dx%5E%7B2m%7D%29%5C%5C%20x_%7B2%7D%20%3D%20x_%7B1%7D%5E%7B2%7D%5C%2Cmod%5C%2Cn%20%5Cquad%20%28%5Cequiv_%7Bn%7Dx%5E%7B4m%7D%29%5C%5C%20%5Ccdots%5C%5C%20x_%7Br%7D%20%3D%20x_%7Br-1%7D%5E%7B2%7D%5C%2Cmod%5C%2Cn%20%5Cquad%20%28%5Cequiv_%7Bn%7Dx%5E%7B2%5E%7Br%7Dm%7D%20%5Cequiv_%7Bn%7D%20x%5E%7Bn-1%7D%29%5C%5C%20%5Ctext%7BSi%20ha%20che%20%7D%20x_%7B0%7D%20%5Cneq%201%20%5Ctext%7B%20e%20inoltre%20%7D%20x_%7Bi%7D%20%5C%2C%21%5Cequiv_%7Bn%7D%20-1%20%5Ctext%7B%20per%20%7D%200%20%5Cleq%20i%20%3C%20r.)

## 4. Algoritmo per la generazione di numeri primi

Una funzione che consente di generare un numero primo casuale di k bit. All’utente viene richiesto di inserire il numero di bit (**k**) con cui generare appunto il numero primo. Anche in questo caso l’utente deve inserire un numero massimo di ***rounds*** per il test di Miller-Rabin che viene invocato all’interno della funzione per la generazione di numeri primi. Come spiegato nel punto precedente è consigliato inserire un numero di ***rounds = 40***.

Nel codice la funzione che esegue l’algoritmo per la generazione di numeri primi è:

```python
def generate_prime(k, rounds=40):
	'''some code'''
	return number
```

Mentre la funzione che imposta i valori dei parametri in input è:

```python
def set_generate_prime():
	'''some code'''
```

In termini matematici si può definire come segue:

![equation](https://latex.codecogs.com/gif.latex?%5Ctext%7BPer%20generare%20casualmente%20un%20numero%20primo%20%7D%20n%20%5Ctext%7B%20dell%27ordine%20di%20%7D%202%5E%7Bk%7D%20%5Ctext%7B%20si%20applica%20il%20seguente%20algoritmo%3A%7D%5C%5C%201.%20%5C%2C%5C%2C%5C%2C%20%5Ctext%7BGenerare%20un%20vettore%20di%20%7D%20k%20%5Ctext%7B%20bit%20casuali%2C%20porre%20il%20bit%20meno%20significativo%20a%201%20%28il%20numero%20deve%20essere%7D%5C%5C%20%5Cquad%5C%2C%5C%2C%20%5Ctext%7Bdispari%29%20e%20quello%20piu%27%20significativo%20a%201%20%28ci%20interessa%20che%20il%20numero%20abbia%20ordine%20di%20grandezza%20%7D%20s%5E%7Bk%7D%29.%5C%5C%20%5Cqquad%20%5Ctext%7BSia%20%7D%20n%20%5Ctext%7B%20il%20numero%20risultante%20espresso%20in%20forma%20binaria%3B%7D%5C%5C%202.%20%5Cquad%20%5Ctext%7BApplicare%20ad%20%7D%20n%20%5Ctext%7B%20un%20test%20di%20primalita%27%3B%7D%5C%5C%203.%20%5Cquad%20%5Ctext%7BSe%20%7D%20n%20%5Ctext%7B%20non%20e%27%20primo%2C%20si%20deve%20tornare%20al%20passo%201%2C%20altrimenti%20si%20conclude%20restituendo%20%7D%20n.)

Questo algoritmo converge abbastanza velocemente → ***n/log(n)***.

## 5. SCHEMA RSA

Se l’utente sceglie la seguente funzione dalla lista delle possibili funzioni nel menù principale, il programma rende a schermo un sotto-menù mostrando tutte le funzioni riguardanti lo schema RSA.

L’utente dunque può scegliere tra una lista di funzioni disponibili che vengono stampate a schermo, semplicemente inserendo il numero corrispondente.

Questo ***sotto-menù*** appare come segue:

![Schermata 2021-05-05 alle 16.19.13.png](https://res.craft.do/user/full/63cec524-c1b6-57b4-8157-df0476f848cb/doc/38F3E494-D23E-4204-B3AC-F14F8DF5026D/F8777E58-3ED5-4894-8477-5F965BCE50B5_2)

In termini matematici i parametri per uno schema RSA sono i seguenti:

![equation](https://latex.codecogs.com/gif.latex?%5Cbullet%20%5Cquad%20p%2Cq%20%5Crightarrow%20%5Ctext%7Bnumeri%20primi%20distinti%20molto%20grandi%2C%20segreti%3B%7D%5C%5C%20%5Cbullet%20%5Cquad%20n%20%3D%20p%20%5Ccdot%20q%20%5Crightarrow%20%5Ctext%7Bmodulo%2C%20pubblico%3B%7D%5C%5C%20%5Cbullet%20%5Cquad%20d%20%3C%20n%20%5Ctext%7B%20relativamente%20primo%20con%20%7D%20%5Cphi%28n%29%3D%28p-1%29%5Ccdot%28q-1%29%20%5Crightarrow%20%5Ctext%7Besponente%20di%20decifratura%2C%20segreto%3B%7D%5C%5C%20%5Cbullet%20%5Cquad%201%20%3C%20e%20%3D%20d%5E%7B-1%7D%5C%2Cmod%5C%2C%5Cphi%28n%29%20%5Crightarrow%20%5Ctext%7Besponente%20di%20cifratura%2C%20pubblico%3B%7D%5C%5C%20%5Cbullet%20%5Cquad%20K%5E%7B&plus;%7D%3D%5Clangle%20e%2Cn%20%5Crangle%20%5Crightarrow%20%5Ctext%7Bchiave%20pubblica%3B%7D%5C%5C%20%5Cbullet%20%5Cquad%20K%5E%7B-%7D%3D%5Clangle%20d%2Cn%20%5Crangle%20%5Crightarrow%20%5Ctext%7Bchiave%20privata.%7D)

Mostriamo dunque adesso una breve descrizione delle seguenti funzioni dello schema RSA e cosa richiedono in input.

### 1. RSA Keys Generator

Funzione che consente all’utente di generare una chiave pubblica e una chiave privata per RSA.

All'utente viene richiesto di inserire il numero di bit (un numero intero), su cui viene generato il modulo **n** della chiave pubblica e privata, e se deve essere utilizzata l'ottimizzazione con ***CRT*** (Chinese Remainder Theorem) o meno, inserendo il carattere 'Y’ per utillizzare CRT oppure 'N' o un qualsiasi altro carattere se non vuole utilizzarlo.

In maniera analoga ai punti precedenti, all’utente viene inoltre chiesto anche il numero massimo di ***rounds*** per il test di Miller-Rabin.

La funzione infine restituisce:

- **chiave pubblica *(e, n)***
- **chiave privata *(d, n)***

Nel codice la funzione che esegue l’algoritmo per la generazione delle chiave per RSA è:

```python
def generate_rsa_keys(k, crt=False, rounds=40):
	'''some code '''
	return public_key, private_key
```

Mentre la funzione che imposta i valori dei parametri in input è:

```python
def set_rsa_keys():
	'''some code'''
```

### 2. RSA Encryption

La funzione di RSA *encryption* consente all’utente di cifrare un messaggio (*plaintext*) **m** tramite lo schema RSA utilizzando la chiave pubblica **e**.

All’utente viene rischiesto in ::input:::

- il messaggio **m** da cifrare (un numero intero).
- la chiave pubblica **e** con cui effettuale l’encryption (ovvero l’esponente pubblico).
- il modulo **n**.

La funzione restituisce dunque in ::output:: il *ciphertext* **c** generato dall’algoritmo.

Nel codice la funzione che esegue l’algoritmo per l’encryption di RSA è:

```python
def rsa_encryption(m, public_key):
	return fast_modular_exponentiation(m, public_key[0], public_key[1])
```

Mentre la funzione che imposta i valori dei parametri in input è:

```python
def set_rsa_encryption():
	'''some code'''
```

In termini matematici l’operazione di *encryption* di RSA avviene nel modo seguente:

![equation](https://latex.codecogs.com/gif.latex?%5Ctext%7BPosto%20%7D%20m%2C%20%5Ctext%7B%20con%20%7D%200%3Cm%3Cn%2C%20%5Ctext%7B%20il%20plaintext%2C%20allora%20l%27encryption%20e%27%3A%7D%5C%5C%20E_%7BK%5E%7B&plus;%7D%7D%28m%29%20%3D%20m%5E%7Be%7D%5C%2Cmod%5C%2Cn)

### 3. RSA Decryption

La funzione di RSA *decryption* consente all’utente di cifrare un *ciphertext* **c** tramite lo schema RSA utilizzando la chiave privata **d**.

All’utente viene rischiesto in ::input:::

- il ciphertext **c** da decifrare (un numero intero);
- la chiave privata **d** con cui effettuale la decryption (ovvero l’esponente privato);
- il modulo **n**.

La funzione restituisce dunque in ::output:: il messaggio (*plaintext*) **m** generato dall’algoritmo.

Nel codice la funzione che esegue l’algoritmo per la decryption di RSA è:

```python
def rsa_decryption(c, private_key, crt=False):
	'''some code'''
	return rsa_encryption(c, private_key)
```

Mentre la funzione che imposta i valori dei parametri in input è:

```python
def set_rsa_decryption():
	'''some code'''
```

In termini matematici l’operazione di *decryption* di RSA avviene nel modo seguente:

![equation](https://latex.codecogs.com/gif.latex?%5Ctext%7BPosto%20%7D%20c%20%5Ctext%7B%20il%20ciphertext%2C%20allora%20la%20decryption%20e%27%3A%7D%5C%5C%20D_%7BK%5E%7B-%7D%7D%28c%29%20%3D%20c%5E%7Bd%7D%5C%2Cmod%5C%2Cn)

### 4. RSA Decryption con e senza CRT (Chinese Remainder Theorem)

Funzione che consente all’utente di testare e confrontare le prestazioni della decifratura RSA con e senza l’ottimizzazione **CRT** (**Chinese Reaminder Theorem**), basandosi sull'*encryption* di un numero ***i*** di *ciphertext* generati casualmente con **k** bits.

All’utente viene richiesto in ::input:::

- i numeri primi **p** e **q** per il caclolo del modulo **n**;
- l’esponente **d** della chiave privata;
- la dimenisone in **k** bits dei singoli ciphertext, che verranno generati casualmente durante il test;
- il numero totale di ciphertext da decifrare (**ciphertext_num**).

La funzione restituisce dunque in ::output:: il tempo di esecuzione totale (in secondi) per la *decryption* dei ciphertext per RSA con e senza ottimizzazione CRT. Infatti attraverso il CRT possiamo manipolare numeri molto grandi di **m**, **e**, **c**, **d** e **n**, facilitando molto i calcoli per l'*encryption* e *decryption* di RSA. Per la formula CRT alcuni valori vanno precomputati.

In termini matematici l’ottimizzazione **CRT** per RSA può essere definita come segue:

![equation](https://latex.codecogs.com/gif.latex?%5Ctext%7BI%20seguenti%20valori%20sono%20precomputati%20e%20memorizzati%20come%20parte%20della%20chiave%20privata%3A%7D%5C%5C%20%5Cbullet%20%5Cquad%20p%20%5Ctext%7B%20e%20%7D%20q%20%5Ctext%7B%3A%20numeri%20primi%20dalla%20generazione%20della%20chiave.%7D%5C%5C%20%5Cbullet%20%5Cquad%20d_%7BP%7D%20%3D%20d%20%5C%2C%5C%2Cmod%5C%2C%28p-1%29%5C%5C%20%5Cbullet%20%5Cquad%20d_%7BQ%7D%20%3D%20d%20%5C%2C%5C%2Cmod%5C%2C%28q-1%29%5C%5C%20%5Cbullet%20%5Cquad%20q_%7Binv%7D%20%3D%20q%5E%7B-1%7D%5C%2C%5C%2Cmod%5C%2Cp%5C%5C%20%5C%5C%20%5Ctext%7BQuesti%20valori%20consentono%20al%20destinatario%20di%20calcolare%20l%27esponenziazione%20%7D%5C%5C%20m%20%3D%20c%5E%7Bd%7D%5C%2C%5C%2Cmod%28p%5Ccdot%20q%29%5C%5C%5Ctext%7Bin%20modo%20piu%27%20efficiente%20come%20segue%3A%7D%5C%5C%20%5Cbullet%20%5Cquad%20m_%7B1%7D%20%3D%20c%5E%7Bd_%7BP%7D%7D%5C%2C%5C%2Cmod%5C%2Cp%5C%5C%20%5Cbullet%20%5Cquad%20m_%7B2%7D%20%3D%20c%5E%7Bd_%7BQ%7D%7D%5C%2C%5C%2Cmod%5C%2Cq%5C%5C%20%5Cbullet%20%5Cquad%20h%20%3D%20q_%7Binv%7D%20%5Ccdot%20%28m_%7B1%7D-m_%7B2%7D%29%5C%2C%5C%2Cmod%5C%2Cp%5C%5C%20%5Cbullet%20%5Cquad%20m%20%3D%20%28m_%7B2%7D%20&plus;%20h%20%5Ccdot%20q%29%5C%2C%5C%2Cmod%5C%2C%28p%20%5Ccdot%20q%29)

Nel codice la funzione che si occupa di precomputare i valori per la formula CRT è:

```python
def crt_pre_computation(p, q, d):
	_, q_inv, _ = extended_euclidean(q, p)
	return d % (p-1), d % (q-1), q_inv % p
```

Mentre la funzione che imposta i valori in input per eseguire il test delle prestazioni con e senza CRT è:

```python
def set_rsa_with_without_crt():
	'''some code'''
```

> **Test di Esempio**

Per eseguire un test di esempio realistico (ovvero con numeri di grandezza dell’ordine 10^100) sono stati scelti i seguenti parametri:

![equation](https://latex.codecogs.com/gif.latex?%5Cbullet%20%5Cquad%20p%20%3D%2011988019892663790245605706324768690328643971620691505564399412103293679%5C%5C%5Cquad%5C%2C%5C%2C%5C%2C%5Cqquad00443056642880169566726653096947795474052817661118289502345520829881543%5C%5C%5Cquad%5C%2C%5C%2C%5C%2C%5Cqquad3594675263457%5C%5C)
![equation](https://latex.codecogs.com/gif.latex?%5Cbullet%20%5Cquad%20q%20%3D%2073437504130820742130231078016485498743814570055198205364815124840443310%5C%5C%5Cquad%5C%2C%5C%2C%5C%2C%5Cqquad78399140180598460065094095658712615608064367840781372121379169340647673%5C%5C%5Cquad%5C%2C%5C%2C%5C%2C%5Cqquad710576772581%5C%5C%20%5Cbullet%20%5Cquad%20d%20%3D%2034099929851810262429239940846935409788295092554098986926683831364649069%5C%5C%5Cquad%5C%2C%5C%2C%5C%2C%5Cqquad96466103783686826238036529359495334362814844764621192304375693814095884%5C%5C%5Cquad%5C%2C%5C%2C%5C%2C%5Cqquad85281669586388068285096434171382421421003351150629956333866520134951886%5C%5C%5Cquad%5C%2C%5C%2C%5C%2C%5Cqquad07854186847538076468534330020245198797555599368679076918784838182099319%5C%5C%5Cquad%5C%2C%5C%2C%5C%2C%5Cqquad327556389466617065226768)
![equation](https://latex.codecogs.com/gif.latex?%5Ctext%7BGenerando%20quindi%20un%20modulo%20%7D%20n%20%3D%20p%20%5Ccdot%20q%5C%5C%20%5Cbullet%20%5Cquad%20n%20%3D%2088037026038785832584708019101520491805733491629912464650859739549458558%5C%5C%5Cquad%5C%2C%5C%2C%5C%2C%5Cqquad29821404056309201812453448938473623627890357015229199337499151648903980%5C%5C%5Cquad%5C%2C%5C%2C%5C%2C%5Cqquad62628861958175036319662905086435922115669787468427683379601206214949730%5C%5C%5Cquad%5C%2C%5C%2C%5C%2C%5Cqquad09218275012169867481928724214874763131621993606887426022134983625966239%5C%5C%5Cquad%5C%2C%5C%2C%5C%2C%5Cqquad169385457575030948872517)


Una volta scelto i parametri è stata testata l’*encryption* RSA basando il test su 100 ciphertext generati casulamente, ciascuno formato da 1024 bits. I risultati ottenuti sono i seguenti:

- **RSA Decryption senza ottimizzazione CRT** → ***0.6689469814300537*** **secondi**.
- **RSA Decryption con ottimizzazione CRT** → ***0.3195810317993164*** **secondi**.

È possibile dunque notare come la decryption RSA con ottimizzazione CRT sia nettamente più veloce dell'approccio senza ottimizazzione CRT, nello specifico caso oltre due volte più veloce. Per numeri piccoli invece i due approcci hanno prestazioni molto simili.

Sperimentalemente comunque andando ad aumentare via via la dimensione dei dati si può concludere che l’approccio con l’ottimizzazione CRT risulta essere fino a quattro volte più veloce dell’approccio senza l’ottimizazzione CRT.

## Run
To run the project:
```
python3 PublicKeyCryptography.py
```