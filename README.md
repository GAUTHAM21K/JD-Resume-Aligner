# Resume Tailor

A powerful Python application that automatically tailors your resume to specific job descriptions using AI. Resume Tailor analyzes job requirements and optimizes your resume's profile, skills, and projects to maximize alignment—generating a targeted resume ready for submission.

## Features

- **AI-Powered Tailoring**: Uses Google's Gemini API to intelligently adapt your resume
- **STAR Method Optimization**: Rewrites project bullets with quantifiable achievements
- **Smart Parsing**: Automatically extracts company names and match scores
- **DOCX Support**: Works with Word documents for professional formatting
- **Multi-Project Support**: Incorporates project files (.md, .txt, .docx) into the tailoring process
- **Clean Output**: Automatically formats generated resumes for presentation

## Requirements

- Python 3.8+
- Google Gemini API key (or OpenRouter API key)
- Required Python packages (see Installation)

## Installation

1. Clone or download this project
2. Install dependencies:
   ```bash
   pip install typer rich requests python-dotenv openai python-docx
   ```

3. Create a `.env` file in the project root with your API key:
   ```
   GEMINI_API_KEY=your_api_key_here
   OPENROUTER_API_KEY=your_alternative_api_key
   ```

## Usage

### Basic Resume Tailoring

1. Prepare your files:
   - `master/resume.docx` - Your master resume
   - `projects/` - Directory with project descriptions (.md, .txt, or .docx files)

2. Run the tailor command:
   ```bash
   python tailor.py start
   ```

3. When prompted, paste your job description and press `Ctrl+D` (or `Ctrl+Z` on Windows)

4. Once complete, your tailored resume will be saved to `tailored_resumes/Resume_[Company_Name].docx`

### Command-Line Options

```bash
python tailor.py start --resume path/to/resume.docx --projects path/to/projects/
```

**Options:**
- `--resume, -r`: Path to your master resume (default: `master/resume.docx`)
- `--projects, -p`: Path to projects directory (default: `projects/`)

## Project Structure

```
.
├── tailor.py              # Main resume tailoring application
├── scaffold.py            # Project scaffolding tool
├── master/
│   └── resume.docx        # Your master resume
├── projects/              # Your project descriptions
│   ├── project1.md
│   ├── project2.md
│   └── ...
├── tailored_resumes/      # Generated tailored resumes
└── .env                   # API credentials (not in repo)
```

## How It Works

1. **Input Processing**: Reads your master resume and job description
2. **Project Collection**: Gathers all project files for context
3. **AI Analysis**: Sends all information to Gemini for intelligent tailoring
4. **Tailoring Optimization**:
   - Preserves original contact info, experience, and academics
   - Customizes profile summary to match job requirements
   - Rewrites skills and competencies for relevance
   - Reimagines projects using the STAR Method (Situation, Task, Action, Result)
5. **Output Generation**: Converts AI output to professional DOCX format
6. **Match Score**: Provides a relevance score (0-100) indicating how well the tailored resume matches the job

## Resume Customization Strategy

Resume Tailor intelligently preserves the core structure while focusing customization where it matters most:

- **Preserved**: Contact information, experience history, academic credentials
- **Tailored**: Profile summary, skills section, project descriptions

This ensures authenticity while maximizing relevance to each opportunity.

## STAR Method Implementation

Projects are rewritten using the STAR framework:
- **S**ituation: Context of the challenge
- **T**ask: Your specific responsibility  
- **A**ction: What you did (with tools/technologies)
- **R**esult: Quantifiable outcomes and impact

Example transformation:
- **Before**: "Built a web application for tracking inventory"
- **After**: "Developed an inventory management system using Python and PostgreSQL, reducing manual data entry by 40% and improving stock accuracy to 99.8%"

## API Options

Resume Tailor supports multiple AI providers:

1. **Gemini API** (Primary)
   - Set `GEMINI_API_KEY` in `.env`
   - High quality, cost-effective

2. **OpenRouter API** (Fallback)
   - Set `OPENROUTER_API_KEY` in `.env`
   - Automatic fallback if Gemini is unavailable

## Output

Generated resumes are saved as `.docx` files in the `tailored_resumes/` directory with the naming format:
```
Resume_[Company_Name].docx
```

The output includes:
- Clean formatting without markdown artifacts
- Proper heading hierarchy
- Bullet-point lists for readability
- Professional Arial font at 10pt

## Troubleshooting

**Issue**: "API key not found"
- Ensure `.env` file exists with your `GEMINI_API_KEY`

**Issue**: Resume output is truncated
- The AI generates the full resume; if truncation occurs, check the input token limit or try a shorter job description

**Issue**: Docx parsing errors
- Ensure master resume is a valid `.docx` file
- Project files should be `.md`, `.txt`, or `.docx` format

**Issue**: Empty response from AI
- Check your API key is valid and has sufficient quota
- Verify internet connection
- Try with a shorter job description

## Advanced Usage

### Using the Scaffold Tool

Create project directory structures:
```bash
python scaffold.py create my_project
```

Then paste your desired structure diagram when prompted.

## License

This project is provided as-is for personal use.

## Support

For issues or questions, check:
1. Your API key configuration in `.env`
2. File paths are correct and accessible
3. All required packages are installed
4. Job description is properly formatted

---

**Resume Tailor v2026** - Optimize your resume, land your role.
