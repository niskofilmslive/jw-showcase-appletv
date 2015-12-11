# JW Player for Apple TV

This app enables you to easily put your JW Player-hosted video content on the new Apple TV with no coding and minimal configuration. It works with any JW Player edition, from Free to Enterprise (note that usage will count against your monthly JW streaming limits).

You can use the app with other content delivery platforms (or your own web server), but you will need to modify the source code.

## Supported features

- Populates your app's media content using RSS feeds. If you are using JW Platform, this happens auto-magically based on playlists that you specify. Using RSS feeds from other sources will require you to hack the source code.
- Video titles, descriptions and hero images populated from RSS feed metadata.
- Playback of HLS and MP4 video content from JW Platform playlists. You can add external URLs (for example, from your own server or CDN) to your playlists in the Content tab of your JW Player account dashboard.
- Customize the user interface with your own branding. The default app is configured for JW Player branding and content but you can easily change this to use your own assets by modifying the config.json file. Advanced customization is possible, but you will need to hack around in the source code.
- Basic playback analytics reporting to JW Player Platform.

### Unsupported Features

Due to the lack of UIWebVuew support in tvOS, the app is not based on the HTML5 JW Player, so some features are not yet implemented. We will continue to add features to the app and always welcome pull requests from the community.

- Advertising (VAST, VPAID, GoogleIMA, etc.)
- Security-related features like encrypted HLS, DRM, tokenized URLs, content sunrising
- Captions

## Usage Instructions (JW Platform integration)

1. Log in to your JW Player dashboard (https://dashboard.jwplayer.com). If you do not have an account, you can create a free one at jwplayer.com.
1. Click Account > API Keys and copy your API key (for example, WT2yg4NU).
1. Click Content > Playlists. Click the title of a playlist that you want to include in your app.
1. In the playlist details page that opens, record the Playlist ID (for example, PQkCnnIH). You can add as many playlists as you want to the app and also specify a "featured" playlist.
1. Clone the JW Player for Apple TV repo.
1. Copy the jwplayer-appletv-web-app directory to your web app server.
1. In the jwplayer-appletv-web-app/resources/configs directory, rename the VCyJXbpY directory to the JW Player API key that you recorded in step 2.
1. Open the config.json file in a text editor and replace the default values with your own. The recommended image sizes are 1920x1080 for the splashScreen image and 1920x400 for the bannerImage.
1. Open the appletv-tvos-app/jwplayer-appletv-app.xcodeproj project in Xcode.
1. Open the AppDelegate.swift file. Change the baseURL variable to your web app server location.
1. Open the info.plist file. Change the jwplayer.account_key value to your JW Player API key.
1. Build the project in Xcode. We recommend running the app in the Xcode emulator to test that everything is configured properly. For instructions on using the emulator, see the Xcode documentation.
1. Submit your app to the Apple App Store. For instructions, see https://developer.apple.com/tvos/submit/

## Requirements

- Apple Xcode 7.1 or later
- A text editor
- An HTTP server (or Amazon S3 bucket, etc.) to host your app's TVML, JavaScript, and config files
- An Apple Developer account (only required if you want to list your app in the Apple Store)
