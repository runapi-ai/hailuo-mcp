# @runapi.ai/hailuo-mcp

RunAPI MCP server for the **Hailuo** model line. Create tasks,
poll their status, and check pricing through a single RunAPI API key.

## Tools

- `image_to_video` — create a Hailuo task (image to video) and (optionally) poll until it reaches a terminal status. Returns the task id, status, output URLs, and a price snapshot. Models: `hailuo-02-image-to-video-pro`, `hailuo-02-image-to-video-standard`, `hailuo-2.3-image-to-video-pro`, `hailuo-2.3-image-to-video-standard`, `hailuo-02-text-to-video-pro`, `hailuo-02-text-to-video-standard`.
- `text_to_video` — create a Hailuo task (text to video) and (optionally) poll until it reaches a terminal status. Returns the task id, status, output URLs, and a price snapshot. Models: `hailuo-02-image-to-video-pro`, `hailuo-02-image-to-video-standard`, `hailuo-2.3-image-to-video-pro`, `hailuo-2.3-image-to-video-standard`, `hailuo-02-text-to-video-pro`, `hailuo-02-text-to-video-standard`.
- `get_task` — fetch the current status and latest payload for a task.
- `check_pricing` — look up pricing for a model in this line.

## Configuration

Set a RunAPI API key via the `RUNAPI_API_KEY` environment variable, or write
it to `~/.config/runapi/config.json`:

```bash
mkdir -p ~/.config/runapi
echo '{"api_key":"YOUR_KEY"}' > ~/.config/runapi/config.json
```

Get an API key at https://runapi.ai. Pricing is listed at
https://runapi.ai/pricing.

## Usage

Run the server over stdio:

```bash
npx -y @runapi.ai/hailuo-mcp
```

Add it to an MCP client (see `examples/` for per-client configs):

```json
{
  "mcpServers": {
    "hailuo": {
      "command": "npx",
      "args": ["-y", "@runapi.ai/hailuo-mcp"],
      "env": { "RUNAPI_API_KEY": "${RUNAPI_API_KEY}" }
    }
  }
}
```

## License

Apache-2.0
