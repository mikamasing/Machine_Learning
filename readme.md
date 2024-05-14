This is a readme-file for my project.

This project serves as a porifolio for my skills as a machine learning 
engineer.


# Analysis of Release Frequency and Popularity on Spotify

## Prosjektbeskrivelse
Dette prosjektet har som mål å analysere hvordan en artists utgivelsesfrekvens (første og siste utgivelsesår, totalt antall utgivelser, og totalt antall spor) påvirker deres popularitet, målt i antall månedlige lyttere.

## Forretningsmål
Forstå hvordan utgivelsesstrategier påvirker en artists popularitet på Spotify for å kunne gi innsikt til artister og plateselskaper om optimal utgivelsesfrekvens for å maksimere popularitet og lytterengasjement.

## Data
- **Datakilder**: Dataset fra Spotify med metadata om artister, inkludert månedlige lyttertall, følgertall, sjangre, utgivelsesår, totalt antall utgivelser, og totalt antall spor.
- **Datatyper**: Strukturerte data i CSV-format.
- **Datakvalitet**: Inneholder både komplette data og rader med manglende verdier. Vi vil bruke CLEANED_Spotify_artist_info.csv for å sikre data med høyere kvalitet.

## Omfang
- **Inkludert**:
  - Data innsamling og rensing.
  - Analyse av sammenheng mellom utgivelsesfrekvens og popularitet.
  - Modellering og evaluering av faktorer som påvirker popularitet.
  - Rapportering og visualisering av funn.
- **Ekskludert**:
  - Implementering i produksjon.
  - Sanntids datahåndtering.

## Interessenter
- Prosjektleder: [Navn]
- Data Scientists: [Navn]
- Forretningsanalytikere: [Navn]
- Artister og plateselskaper som kan dra nytte av innsikten.

## Metodologi
- **Exploratory Data Analysis (EDA)**: Utforske dataene for å forstå distribusjoner, korrelasjoner og trender.
- **Feature Engineering**: Lage nye variabler som representerer utgivelsesfrekvens.
- **Modellvalg**: Bruke lineær regresjon, random forest og decision trees for å modellere sammenhengen mellom utgivelsesfrekvens og popularitet.
- **Evaluering**: Bruke metrikker som R-squared og Mean Squared Error (MSE) for å evaluere modellene.

## Ressurser og Verktøy
- **Personell**: 2 Data Scientists, 1 Data Engineer.
- **Programvare**: Python, Jupyter, Scikit-Learn, Pandas, Matplotlib/Seaborn.
- **Maskinvare**: Cloud Computing via AWS eller lokal maskin med tilstrekkelig kapasitet.

## Tidslinje
- **Uke 1-2**: Datainnsamling og rensing, EDA.
- **Uke 3-4**: Feature Engineering og modellering.
- **Uke 5**: Evaluering og rapportering.

## Risikovurdering
- **Datakvalitet**: Manglende eller uriktige data kan påvirke analysen. Løsning: Rense dataene grundig og bruke metoder for å håndtere manglende verdier.
- **Modellnøyaktighet**: Modellen kan ha lav nøyaktighet. Løsning: Prøve forskjellige modeller og justere hyperparametere.
- **Tidspress**: Stramme tidsfrister kan redusere grundighet. Løsning: Prioritere nøkkeloppgaver og kommunisere tidlig med interessenter om forsinkelser.

## Suksesskriterier
- **Modellens nøyaktighet**: Minimum 80% forklaringsgrad (R-squared) og lav Mean Squared Error (MSE).
- **Innsikt**: Identifisering av klare mønstre og faktorer som påvirker en artists popularitet basert på utgivelsesfrekvens.
- **Tilbakemelding**: Positiv tilbakemelding fra interessenter, spesielt artister og plateselskaper.





About Dataset (Info from [kaggle.com](https://www.kaggle.com/datasets/sarahjeffreson/large-random-spotify-artist-sample-with-metadata?resource=download))
This is a (pseudo) random sample of Spotify artist metadata, including Monthly Listener counts from 2024, follower counts, genres, dates of first and most-recent releases, total number of releases and total number of tracks, as of 2024.

The dataset is designed to be representative of the distribution of all artists on Spotify, without bias towards more well-known/popular artists. This sets it apart from other similar datasets, retrieved using the Spotify Web API.

There are two files: CLEANED_Spotify_artist_info.csv(~15,000 artists) contains only artists/rows with non-null values of all columns but Popularity and Followers (Monthly Listeners is more informative than either of these). The other file, Spotify_artist_info.csv (~37,000 artists) retains the artists/rows with null values in these columns.

All the code associated with the creation of this dataset can be found on my GitHub. See data Provenance (below) for further details.

All suggestions for improvement are very welcome!

Possible usage
This dataset is particularly useful as a baseline/comparison for the exploration of bias, or for any demographic study of artists on Spotify, for example:

Studying how many artists on Spotify are actively-producing music, and at what rate
Comparing Monthly Listener distributions across different genres
In combination with a dataset of artists featured on Editorial playlists, a causal exploration of the factors (and biases) that might lead an artist to be featured on the Editorial playlists
Any other interesting ideas you have - please discuss! 🙏
Column description
ids: Unique Spotify IDs of each artist, str
names: Spotify artist name, str
popularity: The Spotify-defined popularity metric, int
Note that Spotify does not actually disclose how this is calculated, and so this metric should be used with caution. In broad terms, it's calculated from the popularity of an artist's tracks, which in turn is "based, in the most part, on the total number of plays the track has had and how recent those plays are."
followers: The number of followers the artist has, int
genres: The musical genres associated with each artist: where more than one genre is associated with an artist, separate genres are contained within quotation marks and separated by commas; where only one genre is present, no quotations marks are used, str, empty if no genres
Note that genres are often absent from the Spotify metadata, so in CLEANED_Spotify_artist_info.csv, we've done an additional scrape of the Spotify biographies of artists with missing genres, avoiding throwing out an additional 3,000 rows (see Provenance for details)
To use only the genres from the official Spotify metadata, you can apply your own cleaning to Spotify_artist_info.csv
first_release: The year of an artist's first release, int, -1 if no releases
last_release: The year of an artist's most recent release, as of May 2024, int, -1 if no releases
num_releases: The total number of releases an artist has made, as of May 2024, capped at 20 (all numbers >20 are set to 20) int, -1 if no releases
num_tracks: The total number of tracks in albums and singles, not compilations that an artist has released, as of May 2024, int, -1 if no tracks
monthly_listeners: The number of unique monthly listeners for each artist, collected during April and May 2024. This is the most reliable measure of an artist's popularity, that's publicly available on Spotify, float, 0 if absent