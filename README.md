![export](https://github.com/user-attachments/assets/ee379feb-348d-48e7-899c-134f7f7cd74f)

<div class="title-block" style="text-align: center;" align="center">

  [![Discord Community](https://img.shields.io/badge/discord-@elevenlabs-000000.svg?style=for-the-badge&logo=discord&labelColor=000)](https://discord.gg/elevenlabs)
  [![Twitter](https://img.shields.io/badge/Twitter-@elevenlabsio-000000.svg?style=for-the-badge&logo=twitter&labelColor=000)](https://x.com/ElevenLabsDevs)
  [![PyPI](https://img.shields.io/badge/PyPI-elevenlabs--mcp-000000.svg?style=for-the-badge&logo=pypi&labelColor=000)](https://pypi.org/project/elevenlabs-mcp)
  [![Tests](https://img.shields.io/badge/tests-passing-000000.svg?style=for-the-badge&logo=github&labelColor=000)](https://github.com/elevenlabs/elevenlabs-mcp-server/actions/workflows/test.yml)

</div>


<p align="center">
  Official ElevenLabs <a href="https://github.com/modelcontextprotocol">Model Context Protocol (MCP)</a> server that enables interaction with powerful Text to Speech and audio processing APIs. This server allows MCP clients like <a href="https://www.anthropic.com/claude">Claude Desktop</a>, <a href="https://www.cursor.so">Cursor</a>, <a href="https://codeium.com/windsurf">Windsurf</a>, <a href="https://github.com/openai/openai-agents-python">OpenAI Agents</a> and others to generate speech, clone voices, transcribe audio, and more.
</p>

## 🚀 **NEW: Enhanced Conversational AI Capabilities**

### ⚡ **CRITICAL: What We Added to the Original Server**

This is an **ENHANCED VERSION** of the original ElevenLabs MCP server with **COMPLETELY NEW** conversational AI analysis capabilities:

#### 🎤 **BRAND NEW Conversational AI Tools:**
- ✨ **`list_conversations`** - **DIDN'T EXIST BEFORE**: Get comprehensive information about ALL your conversational AI calls with complete metadata, filtering, and pagination
- ✨ **`get_conversation`** - **DIDN'T EXIST BEFORE**: Extract **FULL TRANSCRIPTS** with timestamps, speaker identification, and complete conversation analysis

#### 📊 **Before vs. After:**
- ❌ **Original Server**: No way to access conversation data or transcripts from conversational AI
- ✅ **Enhanced Version**: Complete conversation analysis with full transcript extraction
- ❌ **Original Server**: Basic conversational AI creation without data access  
- ✅ **Enhanced Version**: Comprehensive conversation management and analysis tools

#### 🔧 **Technical Enhancements:**
- **Official Client Integration**: Replaced basic HTTP requests with official ElevenLabs Python SDK
- **Comprehensive Error Handling**: Added robust API integration and fallback mechanisms
- **Full API Coverage**: All conversational AI functionality now uses the official client library

## 🎯 Enhanced by YUV.AI

**Special thanks to [Yuval Avidani](https://linktr.ee/yuvai) from YUV.AI** for the comprehensive enhancement of conversational AI capabilities!

- **Developer**: Yuval Avidani  
- **Company**: YUV.AI  
- **Links**: [Linktree](https://linktr.ee/yuvai) | [X/Twitter](https://x.com/yuvalav) | [Instagram](https://instagram.com/yuval_770)

Yuval significantly enhanced this MCP server with advanced conversational AI tools that provide complete conversation analysis, comprehensive transcriptions, and detailed metadata extraction using the official ElevenLabs client library.

## 🚀 Features

### Core Audio Tools
- **Text-to-Speech**: Convert text to high-quality speech with customizable voice settings
- **Speech-to-Text**: Transcribe audio files with speaker diarization support
- **Voice Cloning**: Create instant voice clones from audio samples
- **Sound Effects**: Generate custom sound effects from text descriptions
- **Audio Isolation**: Isolate speech from background noise
- **Voice Design**: Create and preview new synthetic voices

### 🎤 **NEW: Conversational AI Analysis Tools** ⚡ **THESE ARE COMPLETELY NEW!**
The following tools **DID NOT EXIST** in the original server and provide comprehensive access to all conversation data and transcriptions:

#### `list_conversations` ⚡ **BRAND NEW TOOL**
**Get comprehensive information about all conversational AI calls - THIS FUNCTIONALITY NEVER EXISTED BEFORE**
- Lists all conversations with complete metadata
- Filters by agent, time range, and success status
- Shows conversation IDs, agent details, duration, message counts
- Supports pagination with cursor-based navigation
- **Parameters**:
  - `agent_id`: Filter by specific agent
  - `cursor`: Pagination cursor
  - `page_size`: Results per page (1-100, default 30)
  - `call_start_after_unix`: Filter conversations after timestamp
  - `call_start_before_unix`: Filter conversations before timestamp  
  - `call_successful`: Filter by success status (success/failure/unknown)

#### `get_conversation` ⚡ **BRAND NEW TOOL**
**Get complete conversation details including full transcriptions - TRANSCRIPT ACCESS NEVER EXISTED BEFORE**
- Retrieves comprehensive conversation information
- **Full transcript extraction** with timestamps and speaker identification
- Audio availability information (user audio, response audio)
- Conversation metadata (duration, start time, status)
- Automatic analysis and sentiment data when available
- Smart waiting for conversation completion
- **Parameters**:
  - `conversation_id`: The conversation ID to retrieve
  - `wait_for_completion`: Wait for ongoing conversations (default True)
  - `max_wait_seconds`: Maximum wait time in seconds (default 300)

**Example transcript output**:
```
=== FULL TRANSCRIPT (27 messages) ===
[00:00] AGENT: Hi, I'm Sarah. Before we get started, who am I speaking with?
[00:05] USER: John.
[00:08] AGENT: Nice to meet you, John. Could you briefly describe your role...
```

### Agent Management
- **Create Agents**: Set up conversational AI agents with custom prompts and voices
- **List Agents**: View all available conversational AI agents
- **Agent Details**: Get comprehensive agent configuration and status

### Voice Management
- **Voice Library**: Search and browse the complete ElevenLabs voice library
- **Voice Search**: Find voices by name, description, and categories
- **Voice Details**: Get detailed information about specific voices
- **Voice Creation**: Generate new voices from text descriptions

### Advanced Features
- **Phone Integration**: Make outbound calls via Twilio
- **Knowledge Base**: Add documentation and context to agents
- **Subscription Management**: Monitor API usage and limits
- **Audio Playback**: Play generated audio files locally

## 🔧 Transport Protocol

This MCP server uses **STDIO transport**, providing real-time communication with MCP clients like Claude Desktop through standard input/output streams.

## 📋 Prerequisites

- **Python 3.11+** (Required by ElevenLabs SDK)
- **ElevenLabs API Key** (Get one at [elevenlabs.io](https://elevenlabs.io))
- **Windows** (Batch scripts included for Windows)

## 🛠️ Installation

### 1. Clone the Repository
```bash
git clone https://github.com/hoodini/elevenlabs-mcp.git
cd elevenlabs-mcp
```

### 2. Set Up Virtual Environment
```bash
python -m venv .venv
.venv\Scripts\activate  # Windows
# source .venv/bin/activate  # Linux/Mac
```

### 3. Install Dependencies
```bash
pip install -e .
```

### 4. Configure Claude Desktop

Add to your Claude Desktop configuration file:

**Location**: `%APPDATA%\Claude\claude_desktop_config.json`

```json
{
  "mcpServers": {
    "ElevenLabs": {
      "command": "C:\\path\\to\\elevenlabs-mcp\\run_mcp_server.bat",
      "args": [],
      "cwd": "C:\\path\\to\\elevenlabs-mcp"
    }
  }
}
```

Replace `C:\\path\\to\\elevenlabs-mcp` with your actual project path.

### 5. Set Your API Key

Edit `run_mcp_server.bat` and replace the API key:
```batch
set ELEVENLABS_API_KEY=your_actual_api_key_here
```

## 🎯 Usage Examples

### 🎤 NEW: Conversational AI Analysis (THESE TOOLS ARE BRAND NEW!)
```
# List all recent conversations
Use the list_conversations tool to see all conversational AI calls

# Get detailed conversation with full transcript
Use get_conversation with a specific conversation_id to see:
- Complete conversation transcript with timestamps
- Audio availability information  
- Call metadata and duration
- Success/failure status
```

### Text-to-Speech
```
# Convert text to speech
Use text_to_speech with your text and preferred voice

# Custom voice settings
Adjust stability, similarity_boost, and speed parameters
```

### Voice Cloning
```
# Clone a voice from audio files
Use voice_clone with audio file paths and description

# Create voice from text description
Use text_to_voice to generate voice previews
```

## 🔍 MCP Inspector

Test your server setup with the MCP Inspector:

```bash
npx @modelcontextprotocol/inspector@latest
```

The inspector will help you:
- Verify server connection
- Test individual tools
- Debug configuration issues
- Explore tool capabilities

## 📊 API Coverage

This MCP server provides comprehensive coverage of the ElevenLabs API:

### ✅ Fully Implemented
- **Conversational AI**: Complete conversation management and transcript access ⚡ **NEW ENHANCEMENT**
- **Text-to-Speech**: All voice synthesis capabilities
- **Speech-to-Text**: Audio transcription with diarization
- **Voice Management**: Creation, cloning, and library access
- **Agent Management**: Full conversational AI agent lifecycle
- **Sound Effects**: Custom audio generation
- **Audio Processing**: Isolation and enhancement

### 🎯 Enhanced Features ⚡ **ALL NEW ENHANCEMENTS**
- **Official Client Integration**: Uses the official ElevenLabs Python SDK (**NEW**)
- **Comprehensive Transcripts**: Full conversation analysis with timestamps (**COMPLETELY NEW**)
- **Advanced Filtering**: Multiple filter options for conversation search (**NEW**)
- **Error Handling**: Robust error handling and fallback mechanisms (**ENHANCED**)
- **Windows Integration**: Optimized for Windows development environments (**NEW**)

## 🐛 Troubleshooting

### Common Issues

**"Module not found" errors**:
- Ensure you're using the correct virtual environment
- Verify Python 3.11+ is installed
- Run `pip install -e .` in the project directory

**MCP connection issues**:
- Check that the batch file path is correct in Claude config
- Verify API key is set in the batch file
- Ensure no spaces in file paths cause parsing issues

**Transcript not showing**:
- Verify conversation is completed (`status: done`)
- Check that the conversation has audio content
- Some conversations may not have transcripts available immediately

## 📝 Development

### Building the Package
```bash
python -m build
```

### Running Tests
```bash
python -m pytest tests/
```

### Contributing
1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Run tests and build
5. Submit a pull request

## 📄 License

MIT License - see [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **ElevenLabs** for their excellent AI audio platform and API
- **Anthropic** for the Model Context Protocol specification
- **YUV.AI & Yuval Avidani** for the comprehensive conversational AI enhancements

## 🔗 Links

- [ElevenLabs API Documentation](https://elevenlabs.io/docs)
- [Model Context Protocol](https://modelcontextprotocol.io)
- [YUV.AI Linktree](https://linktr.ee/yuvai)
- [Yuval Avidani X/Twitter](https://x.com/yuvalav)

---

**Made with ❤️ by the community, enhanced by YUV.AI**



