# 🎨 From Template to Cartoon: ComfyUI + MiniMax H3 on Runpod

**Turn a photo into a 5-second cartoon with voices, music, and sound effects, using the ComfyUI template on Runpod and changing only two things.**

A coworker snapped a photo of our conference booth. Using the MiniMax H3 workflow in ComfyUI, that photo became a hand-drawn-style cartoon where the booth staff welcomes a visitor, the visitor gives a thumbs-up, and everyone waves goodbye.

**[▶ Watch the video](media/booth-cartoon.mp4)** · **[📊 Slides](media/comfyui-runpod-slides.pdf)**

## What's in this repo

| File | What it is |
| --- | --- |
| [`PROMPT.md`](PROMPT.md) | The full prompt, ready to paste |
| [`workflow/minimax_h3_booth_cartoon.json`](workflow/minimax_h3_booth_cartoon.json) | The exact ComfyUI workflow that made the video (drag it onto the ComfyUI canvas to load it) |
| [`media/booth-cartoon.mp4`](media/booth-cartoon.mp4) | The finished video |
| [`media/comfyui-runpod-slides.pdf`](media/comfyui-runpod-slides.pdf) | The slides (PDF) |

## What the template gives you out of the box

The MiniMax H3 image-to-video template ships with:

- **Sample image:** a transparent RGB gaming mouse, used as the video's first frame
- **Default prompt:** a dark product film with a black studio, blue and orange neon light, and three shots
- **Default settings:** 1:1 square at 0.4 MP, 5 seconds with audio, turbo mode off

## I changed two things. Everything else stayed default

| | Change |
| --- | --- |
| **The photo** | Swapped the sample gaming mouse for a photo of our booth |
| **The prompt** | Rewrote the style, subject, shots, and audio |
| **Left as default** | Resolution, length, models, seed, and turbo setting |

### The key lines from the prompt

- **Style:** "Playful 2D cartoon animation in a bright, hand-drawn animated-series style"
- **Subject:** "Preserve the booth layout, people, clothing colors … and existing runpod branding"
- **Guardrail:** "No computer mice or product close-ups"

### Keeping the dialogue in English

Early versions didn't reliably come out in English: the voices and the speech-bubble text would drift into other languages or invented words. The fix was a dedicated dialogue block that pins down exactly what can be said and shown:

> All spoken dialogue must be in English, using only the exact lines below. Use comic-style speech bubbles with clear, readable English text that exactly matches the spoken dialogue. … No extra dialogue, invented words, subtitles, captions, or decorative text.

Each spoken line is then repeated as a "Matching speech bubble", and the audio section asks for "Clear English voices in the foreground" over "conference ambience without recognizable words." If you adapt this prompt for your own photo, keep that block.

### Same structure as the template, new story

| Template's shots | My shots |
| --- | --- |
| Push-in on the mouse | Push-in on the booth: "Welcome to Runpod!" |
| Scroll-wheel macro | Thumbs-up from a visitor: "Great to be here!" |
| Levitating mouse | Wide, waving freeze-frame |
| Sub-bass and clicks | Cartoon music, pops, and boings |

Three shots and an audio cue, in the same order. Borrowing the template's structure is what made the rewrite quick.

## Try it yourself

1. **Deploy the ComfyUI template on Runpod.** Open the [Runpod console](https://console.runpod.io), choose the ComfyUI template, and deploy a pod.
2. **Load the workflow.** Open ComfyUI from the pod's connect menu and either pick the MiniMax H3 image-to-video template or drag [`workflow/minimax_h3_booth_cartoon.json`](workflow/minimax_h3_booth_cartoon.json) onto the canvas. The workflow's notes list the model files it needs and the folders they go in.
3. **Swap the photo.** Upload your own image in the **Load Image** node. This becomes the first frame.
4. **Swap the prompt.** Paste [`PROMPT.md`](PROMPT.md) into the MiniMax H3 node and edit the scene, shots, and dialogue to match your photo.
5. **Queue the prompt.** The video is saved under `output/video/`.

ComfyUI also exposes an HTTP API on the same pod, so once you're happy with a workflow you can export it with **Export (API)** and queue runs from code instead of the UI.

## Learn more

- [MiniMax H3: the open-weight omni-modal video model and what it takes to run it](https://www.runpod.io/blog/minimax-h3-the-open-weight-omni-modal-video-model-and-what-it-takes-to-run-it)
- [Slides for this demo](media/comfyui-runpod-slides.pdf)
- Questions, or want to see what others are building? [Join the Runpod Discord](https://discord.com/invite/runpod)
