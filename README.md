# EEG_fear_visualisation
Attempt at (live) fear visualisation

> [!WARNING]
> De dataset is heel groot. Wanneer deze meerdere keren wordt gekopieerd, is er een grote kans dat je geheugen vol geraakt. In dat geval crasht de jupyter notebook server. Mijn workaround is om data die niet meer wordt gebruikt te verwijderen.
> ```Python
> del eeg_data_np
> del eeg_data_df
> del df
> ```

De `code_csv.ipynb` bevat een jupiter notebook met een poging om de .csv versie van de EEG data te verwerken.
Ik heb ook een poging ondernomen met de .mat versie van de data, maar heb snel opgegeven. Die code kan je vinden bij `code_mat.ipynb`

Initieel plan van aanpak:

- [x] Laadt de data in 
- [x] Open de data met de MNE package
- [x] Plot de data RAW, misschien is er al iets te zien
- [x] Do preprocessing 
  - [x] high pass > 80Hz omdat de alpha en beta bands die interessant zijn hier ver onder liggen
  - [x] low pass < 0.1Hz om trage drift uit het signaal weg te filteren
  - [x] resampling op 200Hz ipv 1000Hz om berekeningen sneller te laten gebeuren 
  - [x] set reference op channel 129. Dit kanaal werd als reference ingesteld bij het onderzoek. Het advies was wel om de reference te vervangen door 'average' (zo in te vullen in de set_eeg_reference functie). Dit leek visueel niet veel betere resultaten te geven (jupyter notebook)
- [ ] Get frequentie spectrum van elk kanaal. Aangezien we verwachten dat er demodulatie ontstaat in ofwel de alfa band ofwel de beta band, moet er in het frequentiespectrum worden gewerkt. 
- [ ] Plot het frequentiespectrum voor elk kanaal 
- [ ] Plot de muziek op een manier dat een link met de eeg visueel duidelijk zou zijn

## het frequentiespectrum
[Dit artikel](https://pmc.ncbi.nlm.nih.gov/articles/PMC6200158/) vond een correlatie tussen de beta waves (15-23 Hz) en ervaren angst/stress. Mijn initiele idee was om dit exacte process te proberen repliceren. Echter kan ervan worden uitgegaan dat de onderzoeker bij wie de EEG werd afgenomen niet echt emotioneel bewogen was. Kan nog steeds de moeite zijn om eens te bekijken, aangezien het principe sowieso hetzelfde zal zijn voor andere resultaten.

Volgens de onderzoekers zou een trace van de aplha bands interessanter zijn. Dit leek hen alleszins al het geval toen ze de data met het blote oog bestudeerden.