# Product Image Gallery Extractor

A front-end HTML/JS application (no backend required) that extracts product images from vendor URLs provided in a CSV file.

![App Screenshot](https://github.com/user-attachments/assets/6011b88c-8ce2-40ba-93cd-e879fc81504e)

## Features

- **CSV Upload**: Upload a CSV file with product names and URLs
- **Browser-based Parsing**: All CSV parsing happens in the browser
- **CORS-safe Fetching**: Uses multiple public CORS proxies with automatic fallback
- **Smart Image Extraction**: Extracts images from `src`, `data-src`, `srcset`, and background styles
- **Visual Gallery**: Displays a card per product with name, link, and image thumbnails
- **Progress Tracking**: Real-time progress bar and status updates
- **Error Handling**: Graceful handling of fetch failures with retry logic

## Usage

1. Open `index.html` in a web browser
2. Prepare a CSV file with the following columns:
   - `name` (or `product_name`, `title`): Product name
   - `url` (or `link`, `vendor_product_url`, `product_url`): The URL to the product page
3. Click "Choose File" and select your CSV
4. Click "Start Extraction" to begin processing
5. View the results as product cards with extracted image thumbnails

## CSV Format Example

```csv
name,url
"Product A","https://example.com/product-a"
"Product B","https://example.com/product-b"
```

## Technical Details

### CORS Proxies
The app uses multiple CORS proxy services with automatic fallback:
1. [allorigins.win](https://allorigins.win/)
2. [corsproxy.io](https://corsproxy.io/)
3. [codetabs.com](https://codetabs.com/)

### Image Extraction
- Extracts from `<img>` tags: `src`, `data-src`, `data-lazy-src`, `data-original`, `srcset`
- Extracts from CSS background images
- Filters out placeholders, icons, logos, and tracking pixels
- Supports JPG, JPEG, PNG, WebP, GIF, and AVIF formats

### Features
- Request timeout handling (15 seconds)
- Exponential backoff for rate limiting
- Lazy loading for image thumbnails
- XSS protection via HTML escaping

## Requirements

- A modern web browser (Chrome, Firefox, Safari, Edge)
- No server or build tools required
- Just open `index.html` and start using!
