# Open-Source Reverse Engineering Tool (OSRET)

> Note: this project is in the proposal stage and goes not have code yet

OSRET is a command-line tool that uses [Puppeteer](https://github.com/puppeteer/puppeteer) to automate the process of reverse engineering open-source web applications. It allows developers to interact with the app, capture and associate network requests with elements in the UI, and generate example requests and infer response types.

## Features
- Automatically captures and associates network requests with elements in the UI.
- Generates example requests with inferred payloads.
- Infers response types.
- Generates API documentation and code snippets in different languages.
- Can be used headless and integrated into a pipeline.
- Can automate testing.

## Requirements
- Node.js v12+
- npm v6+

## Installation
```sh
npm install -g osret
```

## Usage
```sh
osret <url>
```

This will open a new instance of Chromium, navigate to the provided url, and start capturing network requests.

### Optional arguments
- `--output` : specify the output format. Available options are `json`, `html`, and `md` (default is `json`).
- `--output-file` : specify the output file name. (default is `osret_output.json`)
- `--headless` : run the tool in headless mode. (default is `false`)

## Example
```sh
osret https://google.com --output=json --output-file=google_api.json --headless
```

This command will open a headless instance of Chromium, navigate to https://google.com, capture network requests and generate a json file named `google_api.json` in the current directory with the captured requests and inferred data.

## Output format
The output file will contain an array of requests, each request object will have the following properties:
- `url` : the requested url.
- `method` : the request method.
- `headers` : the request headers.
- `payload` : the request payload (if exists).
- `status` : the response status.
- `response` : the response payload.
