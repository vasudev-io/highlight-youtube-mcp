# YouTube Integration

The YouTube MCP server provides functionality to extract transcripts from YouTube videos.

## Available Tools

### get_youtube_transcript
Retrieves the transcript text from a YouTube video.

**Parameters**:
- `videoUrl`: Full YouTube video URL (supports standard, shortened, and embed URLs)

**Returns**: Object containing:
- `content`: Array with transcript text

### download_youtube_video
Downloads a YouTube video.

**Parameters**:
- `videoUrl`: Full YouTube video URL (supports standard, shortened, and embed URLs)

**Returns**: Object containing:
- `filePath`: Path to the downloaded video file

## URL Support

Handles multiple YouTube URL formats:
- Standard: `https://www.youtube.com/watch?v=VIDEO_ID`
- Shortened: `https://youtu.be/VIDEO_ID`
- Embed: `https://www.youtube.com/embed/VIDEO_ID`

## Error Handling

The server implements standard error handling:
- Invalid URLs return `ErrorCode.InvalidParams`
- Missing URL returns `ErrorCode.InvalidParams`
- Failed transcript fetches return formatted error messages
- Graceful shutdown on SIGINT

## Technical Details

- Built using the Highlight AI MCP SDK
- Uses youtube-transcript library
- Input validation via Zod
- Runs as a stdio-based MCP server
- Supports Node.js >=18.0.0

## Limitations

- Only works with videos that have captions enabled
- Currently only returns English transcripts
- Rate limits depend on YouTube's API restrictions

## Testing the Tools

To test the `get_youtube_transcript` tool, you can use the following steps:
1. Start the server by running `npm start`.
2. Send a request to the server with the `get_youtube_transcript` tool and a valid YouTube video URL.
3. Verify that the response contains the transcript text.

To test the `download_youtube_video` tool, you can use the following steps:
1. Start the server by running `npm start`.
2. Send a request to the server with the `download_youtube_video` tool and a valid YouTube video URL.
3. Verify that the response contains the file path to the downloaded video.
4. Check the specified file path to ensure the video has been downloaded correctly.
