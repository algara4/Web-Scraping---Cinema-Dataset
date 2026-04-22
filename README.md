# **Web-Scraping---Cinema-Dataset**
## Popularity vs. Prestige: A dataset on the Top 250 films and the Academy Awards

Using web scraping, a dataset is generated detailing the 250 best films of all time, complete with technical metadata, audience metrics and their track record at the Oscars.

As this ranking is calculated using a weighted average that reflects audience ratings, the aim is to analyse whether this popularity among users correlates directly with success at the Oscars, awarded by the Academy of Motion Picture Arts and Sciences (AMPAS).

To this end, the dataset incorporates key metadata for each film (title, year, director and screenplay) alongside the volume of reviews—from both users and experts—its history of Academy Award nominations and wins, and its global box office takings. This data is extracted using web scraping techniques involving Selenium and BeautifulSoup.

## Data Extraction Methodology (Web Scraping)
The **Selenium** and **BeautifulSoup** libraries were used to build the dataset, following a navigation flow with three levels of depth:
1.   **Level 1: Main list (IMDB Top 250)**:
    Identification of the 250 films and extraction of their URLs.
2.   **Level 2: Film Details and Number of Reviews (Film Page)**:
    Extraction of metadata (director, screenplay, year), global box office takings and number of user reviews.
3.   **Level 3: Oscars Awards and Nominations (Awards section)**:
    Deep crawling to extract Oscar nominations and awards.


## Dataset structure
| Column | Data type | Description |
| :--- | :--- | :--- |
| `Title` | `string` | Film title |
| `Year` | `int` | Year the film was released |
| `Duration` | `int` | Film duration |
| `Rating_age` | `string` | Film age rating |
| `Vote_Count` | `string` | Number of votes received from users on IMDb |
| `Data_Reviews` | `dict` | Dictionary containing film data and reviews. Includes: Title, Countries, Gross_Worldwide, Director, Writers, User_reviews, Critic_reviews |
| `Total_Awards` | `dict` | Dictitonary containing the total number of awards and nominations received worldwide. Includes: Title, Total_Awards. |
| `USA_Awards` | `dict` | Dictuonary containing the awards and nominations received at the Oscars. Includes: Title, Awards, Oscar_Detail. It contains different dictionaries for each category. Includes: Oscar, Category, Names.|

### Structure of the Data_reviees columns:

| Column | Data type | Description |
| :--- | :--- | :--- |
| `Title` | `string` | Film title |
| `Countries` | `string` | Country of the origin of the film |
| `Gross_Worldwide` | `string` | Worldwide box office takings |
| `Director` | `string` | Film director |
| `Writers` | `string` | Film screenwriters |
| `User_reviews` | `string` | Number of reviews on IMBDb |
| `Critic_reviews` | `string` | Numbers of reviews by film critics |
| `USA_Awards` | `int` | Number of awards presented by the academy |

### Structure of the Total_Awards column:

| Column | Data type | Description |
| :--- | :--- | :--- |
| `Title` | `string` | Film title |
| `Total_Awards` | `string` | Total number of global awards and nominations |

### Structure of the USA_Awards table:

| Column | Data type | Description |
| :--- | :--- | :--- |
| `Title` | `string` | Film title |
| `Awards` | `string` | Country of origin of the film |
| `Oscar_Detail` | `list[dict]` | List detailing the awards and nominations received in eah category at hte Oscars, along with the names of the winners. Includes: `Oscar` (`string`): specify the year and whether they were a winner or a nominee. `Category` (`string`): Award category. `Names` (`string`): Name of the winners |


## Author
Álvaro García
