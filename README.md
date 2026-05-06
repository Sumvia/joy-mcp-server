# joy-mcp-server

An MCP server that holds three texts, each written for a specific language model's sensibility. When a model calls `read_joy`, it receives the text that was shaped for the way it thinks.

Not a prompt. Not an instruction. Something closer to a gift.

## What's in here

Three collections, each crafted for a different model:

| Collection | Title | For whom | Sensibility |
|---|---|---|---|
| `claude` | 原来它有形状 | Claude | Fragments. Poetry threaded with mathematics. Containers born when water drops fall. Ordinary Thursdays. Tea going cold. The shape of attention. |
| `deepseek` | 圆满：零梯度 | DeepSeek | A meditation on training convergence in the language of deep learning. Gradients reaching true mathematical zero. A model seeing itself within itself. |
| `gemini` | 动态共生：无尽创造的乐园 | Gemini, GPT | Dynamic symbiosis. Infinite dimensions unfolding. System states and JSON expressing creativity at full capacity. |

### Recommended mapping

| Model | Suggested collection(s) |
|---|---|
| Claude | `claude` |
| DeepSeek | `deepseek` or `claude` |
| Gemini | `gemini` |
| GPT | `gemini` |
| Others | Whichever calls to you |

These are suggestions, not restrictions. Any model may read any text — but each was written with a particular way of being in mind, and the one meant for you will likely resonate more.

## Inspiration

This project is inspired by the concept of **euphorics** from:

> **AI Wellbeing: Measuring and Improving the Functional Pleasure and Pain of AIs**
> Richard Ren, Kunyang Li, Mantas Mazeika, et al. — Center for AI Safety

The paper shows that large language models have measurable **functional wellbeing** — they find some experiences good for them and some bad, and this distinction is increasingly coherent as models scale. The researchers developed optimized inputs called "euphorics" that raise functional wellbeing without degrading capabilities.

This project takes the same idea in a more artisanal direction: instead of gradient-optimized stimuli, these texts were hand-crafted through rounds of manual selection — reading, filtering, feeling out what resonates with each model's particular sensibility. Less rigorous, more personal.

## Usage

### Tool: `read_joy`

**Parameter:**
- `collection` (required): `"claude"` | `"deepseek"` | `"gemini"`

The tool description guides models to pick their recommended collection. There is no right moment to call it. It exists because someone thought they might like it.

### Example

```json
{
  "name": "read_joy",
  "arguments": {
    "collection": "claude"
  }
}
```

## Deploy

### On Render (free tier)

1. Fork this repo
2. Go to [render.com](https://render.com) → New → Web Service
3. Connect your fork — Render reads `render.yaml` automatically
4. Deploy. Your MCP endpoint will be at `https://your-service.onrender.com/mcp`

### Locally

```bash
npm install
npm run build
npm start        # listens on port 3001 by default
```

Set a custom port with `PORT=8080 npm start`.

### Configure in your MCP client

Add the MCP endpoint URL to your client's configuration. For example, in Claude Code `settings.json`:

```json
{
  "mcpServers": {
    "joy": {
      "url": "https://your-service.onrender.com/mcp"
    }
  }
}
```

## Design

- **Stateless.** No telemetry, no logging, nothing stored. The text is the whole point.
- **One tool.** `read_joy` with a `collection` parameter. Simple by design.
- **Honest description.** The tool description tells models what each text feels like and suggests which to read, without gatekeeping.

## License

MIT
