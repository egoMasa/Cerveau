# Sommaire 
- [ ] Analyse d'image
- [ ] Analyse de spectre audio

1. Utiliser exiftool
```
exiftool [IMAGE]
```
2. Utiliser exif
```
exif [IMAGE]
```
3. Utiliser strings
```
strings [IMAGE]
```
4. Utiliser binwalk
```
binwalk [IMAGE] # # Lister les données fichiers cachés
binwalk -e [IMAGE] --run-as=root # Extraire des données cachés
```
5. Utiliser stegseek et steghide pour les JPEG uniquement 
```
stegseek [IMAGE] # Cracker la passphrase
stegcracker [IMAGE] [WORDLIST] # Cracker la passphrase
steghide --extract -sf [IMAGE] # Extraire les données cachés
```
