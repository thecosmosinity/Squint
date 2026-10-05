# Squint

A tool for running the modern web on legacy iOS
Get releases from the releases tab, as it is raw python, there is no need to use the repository for source.

## Status

Alpha. Squint currently loads pages, parses their text, and shrinks images. Nothing beyond that works yet (no JavaScript-heavy sites, search, or logins).

## How it works

1. Enter a URL in Squint on your old device.
2. A server on a modern machine downloads the page over HTTPS into `temp/`.
3. The readable content is extracted and stripped down to plain HTML.
4. Links are rewritten to stay inside Squint, and images are resized to small JPEGs.
5. The result is saved to `temp/out/` and served back to the device.

The **clear cache** button wipes `temp/`.

## Requirements

Run the server on a modern device with Python 3.13+. Tested with an iPod touch 3rd gen on iOS 4.3.5.

## Run

```
pip install flask httpx trafilatura pillow
cd run
python main.py
```

Then open `http://<computer-ip>:8080` on the old device and enter a URL, e.g. `en.wikipedia.org/wiki/IPod_Touch`.

Only use it on a trusted local network, since there is no login.
