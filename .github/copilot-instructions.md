# Copilot Instructions for stable-diffusion-webui

## Project Overview
- This is a web UI for Stable Diffusion, primarily using Python and Gradio for the backend, with JavaScript/HTML/CSS for the frontend.
- Major features include txt2img, img2img, outpainting, inpainting, upscaling, prompt matrix, textual inversion, and extensive extension support.
- Core logic is in `webui.py`, with supporting modules in `modules/` and configuration in `configs/`.
- Extensions are loaded from `extensions/` and `extensions-builtin/`.

## Architecture & Data Flow
- The backend (Python) exposes endpoints and UI via Gradio, orchestrating model inference and image processing.
- Frontend assets are in `html/`, `javascript/`, and `style.css`.
- Models and embeddings are stored in `models/` and `embeddings/`.
- Configurations for different model types are in `configs/`.
- External tools (GFPGAN, CodeFormer, ESRGAN, etc.) are integrated via modules and can be toggled in the UI.

## Developer Workflows
- **Run locally:** Use `webui-user.bat` (Windows) or `webui-user.sh` (Linux/macOS) to start the server. Custom options can be set in these scripts.
- **Dependencies:** Install via `requirements.txt` (Python 3.10.x required for torch). For GPU-specific dependencies, see `requirements_versions.txt` and wiki links in README.
- **Extensions:** Place custom extensions in `extensions/`. Built-in extensions are in `extensions-builtin/`.
- **Testing:** Tests are in `test/`. No standard test runner; inspect test files for invocation patterns.
- **Debugging:** Use Gradio's live reload and Python logging. Many modules have verbose/debug options.

## Project-Specific Conventions
- **Prompt attention:** Use `((...))` or `(...:weight)` for emphasis in prompts.
- **Config overrides:** Many UI defaults can be changed via text config files or command-line args in launch scripts.
- **Image metadata:** Generation parameters are saved in PNG chunks or JPEG EXIF; can be restored via UI drag-and-drop.
- **Extensions:** Must follow the extension API as seen in `modules/extensions.py`.
- **Model formats:** Supports safetensors and standard checkpoint formats.

## Integration Points
- **External models/tools:** Integrated via dedicated modules (see `modules/` for GFPGAN, ESRGAN, etc.).
- **API:** Exposed for automation; see `webui.py` and wiki for endpoints.
- **Community scripts:** Supported via the custom scripts tab and extension system.

## Examples
- To add a new upscaler, create a module in `modules/`, update UI in `html/` and `javascript/`, and register in `webui.py`.
- To add a new extension, place it in `extensions/` and follow the API in `modules/extensions.py`.

## References
- See `README.md` and the [project wiki](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki) for detailed documentation and GPU-specific setup.
- For licensing, see `html/licenses.html` and the Settings -> Licenses screen.

---
**Feedback:** Please review and suggest improvements or clarify any missing/unclear sections for your workflow.
