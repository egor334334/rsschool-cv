# 1. Name: Egor Adashkevich

# 2. Contacts:
## * Mobile phone: +375-29-706-08-06
## * Email: egor334@gmail.com

# 3. Brief information about me:
## * my goal is to become a high-class IT specialist;
## * purposeful, quickly absorb information;
## *construction expert, road construction engineer (current position)
# 4. Skills:
## * Python language basic
# 5. Code example (Python)

import requests
from bs4 import BeautifulSoup
URL=r'https://www.last.fm/charts'

class Parser:
    def __init__(self):
        self.session=requests.Session()

    def get_chart(self):
        response=self.session.get(URL)
        return response.text

    @staticmethod
    def _parse_chart(songs: list, autors: list):
        response = []
        for song, author in zip(songs, autors):
            data = {'song': song.string, 'author': author.string}
            response.append(data)
        return response

    def parse_chart(self):
        content=self.get_chart()
        soup=BeautifulSoup(content, 'html.parser')
        song_class='link-block-target'
        author_class='globalchart-track-artist-name'
        songs=soup.find_all('a', {'class':song_class})
        authors = soup.find_all('td', {'class': author_class})
        return self._parse_chart(songs, authors)

[example](https://github.com/egor334334/pythonProject/blob/master/chart/chart_parser.py)
# 6. Education:
* higher education (BNTU (Belarusian National Technical University)- road construction engineer)
* Python language basics (IBA-group)

# 7. Language level: 
* English was studied at school and at university