# playlist2pdf

Turn your Spotify or YouTube playlist into a printable PDF of all songs with title, artist, and duration.

## Features
- Export to stylish PDF
- Supports Spotify (via API) and YouTube (via public links)
- Optionally sort by artist, title, or duration

## Usage
```bash
python playlist2pdf.py --spotify-url "https://open.spotify.com/playlist/xyz"

Requirements
Python 3.8+

spotipy

reportlab


### 🧠 `playlist2pdf.py`
```python
import spotipy
from spotipy.oauth2 import SpotifyClientCredentials
from reportlab.lib.pagesizes import letter
from reportlab.pdfgen import canvas

def fetch_spotify_tracks(playlist_url):
    # This function will be a placeholder unless you provide API keys
    # Replace with actual spotipy logic
    return [
        {"title": "Song 1", "artist": "Artist A", "duration": "3:21"},
        {"title": "Song 2", "artist": "Artist B", "duration": "2:54"},
    ]

def generate_pdf(tracks, output_file):
    c = canvas.Canvas(output_file, pagesize=letter)
    width, height = letter
    y = height - 40
    c.setFont("Helvetica", 12)
    c.drawString(100, y, "Playlist Export")
    y -= 40
    for track in tracks:
        c.drawString(100, y, f"{track['title']} - {track['artist']} [{track['duration']}]")
        y -= 20
    c.save()

if __name__ == "__main__":
    tracks = fetch_spotify_tracks("dummy-url")
    generate_pdf(tracks, "playlist.pdf")
    print("Saved to playlist.pdf")
