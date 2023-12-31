# AsyncPexelsClient

AsyncPexelsClient is an asynchronous Python client for the Pexels API. It allows you to interact with the Pexels API to search for photos and videos, get details of a specific photo or video, get curated and popular photos, and download a specific photo or video.

## Installation

You can install the AsyncPexelsClient using pip:

```bash
pip install pexels-async-api
```

## Usage
First, import the `AsyncPexelsClient` class from the pexels-async-api module:

```python
from pexels_async_api.client import AsyncPexelsClient
```

Then, create an instance of the `AsyncPexelsClient` class, passing your Pexels API key as a parameter to the constructor:

```python
client = AsyncPexelsClient("your_api_key")
```

Now, you can use the `client` object to interact with the Pexels API. Here are some examples:

```python
# Search for photos of cats
photos = await client.search_photos("cats", per_page=5, page=1)
print(photos)

# Search for videos of dogs
videos = await client.search_videos("dogs", per_page=5, page=1)
print(videos)

# Get details of a specific photo by its ID
photo = await client.get_photo(123456)  # replace 123456 with the actual photo ID
print(photo)

# Get details of a specific video by its ID
video = await client.get_video(123456)  # replace 123456 with the actual video ID
print(video)

# Get curated photos
curated_photos = await client.get_curated_photos(per_page=5, page=1)
print(curated_photos)

# Get popular photos
popular_photos = await client.get_popular_photos(per_page=5, page=1)
print(popular_photos)

# Download a specific photo by its ID
photo_data = await client.download_photo(123456)  # replace 123456 with the actual photo ID
with open("photo.jpg", "wb") as f:
    f.write(photo_data)

# Download a specific video by its ID
video_data = await client.download_video(123456)  # replace 123456 with the actual video ID
with open("video.mp4", "wb") as f:
    f.write(video_data)
```

Remember to replace `your_api_key` with your actual Pexels API key. Also, replace `123456` with the actual ID of the photo or video you want to get or download.

## Additional Arguments for Search Functions
The `search_photos` and `search_videos` methods allow you to search for photos and videos on Pexels. Here are the parameters for these methods:

- `query` (string - required): The search query. This is what you're searching for. For example, "cats" or "dogs".

- `per_page` (integer - optional): The number of items to return per page. The maximum is 80. If not provided, the default is 15.

- `page` (integer - optional): The page number to return. If not provided, the default is 1.

- `orientation` (string - optional): The desired photo or video orientation. The current supported orientations are: "landscape", "portrait", or "square".

- `size` (string - optional): The minimum photo or video size. The current supported sizes are: large (24MP), medium (12MP), or small (4MP).

- `locale` (string - optional): The locale of the search you are performing. The current supported locales are: "en-US", "pt-BR", "es-ES", "ca-ES", "de-DE", "it-IT", "fr-FR", "sv-SE", "id-ID", "pl-PL", "ja-JP", "zh-TW", "zh-CN", "ko-KR", "th-TH", "nl-NL", "hu-HU", "vi-VN", "cs-CZ", "da-DK", "fi-FI", "uk-UA", "el-GR", "ro-RO", "nb-NO", "sk-SK", "tr-TR", "ru-RU".

Here's an example of how to use these methods:

```python
import asyncio
from pexels_async_api.client import AsyncPexelsClient

async def main():
    client = AsyncPexelsClient("your_api_key")  # replace "your_api_key" with your actual Pexels API key
    photos = await client.search_photos("cats", per_page=5, page=1)
    print(photos)

# Run the main function
asyncio.run(main())
```

## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License
MIT
