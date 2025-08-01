## 🧠 Multi-Agent Market Research Analyst and Writer with CrewAI
This project demonstrates how to build a multi-agent AI system using CrewAI, where a Market Research Analyst agent collaborates with a Content Writer agent to generate insightful, up-to-date blog content about the AI industry. It integrates CrewAI tools, Serper.dev, Langfuse observability, and OpenLit tracing.

🚀 What This Project Does
This system uses two autonomous AI agents:

Market Research Analyst – Performs real-time market analysis using search and website tools

Content Writer – Generates a blog post based on the research and past writing style

The result: A markdown-formatted, engaging, and informative blog post saved to the /blog-posts directory.

🛠️ Technologies Used
Component	Purpose
CrewAI	Manages agents, tasks, and their workflow
SerperDevTool	Google-like search tool for real-time info
Langfuse	Observability and tracing for LLM agents
OpenLit	Lightweight LLM tracing
Pydantic	Data validation and tool configurations
Markdown	Blog post output format

🧩 Project Structure
bash
Copy
Edit
.
├── app.py                   # Main code
├── blog-posts/             # Directory for blog output
│   ├── new_post.md         # Final blog post
├── .env                    # Environment variables
├── requirements.txt        # Project dependencies
├── README.md               # Project documentation
📦 Installation & Setup
1. Clone the Repository
bash
Copy
Edit
git clone https://github.com/yourusername/crewai-blog-writer
cd crewai-blog-writer
2. Create a Virtual Environment (Optional)
bash
Copy
Edit
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
3. Install Dependencies
bash
Copy
Edit
pip install -r requirements.txt
Or, install manually:

bash
Copy
Edit
pip install langfuse openlit crewai crewai_tools
pip install transformers -U
4. Set Up Environment Variables
Create a .env file in the root directory:

env
Copy
Edit
OPENAI_API_KEY=your-openai-api-key
SERPER_API_KEY=your-serper-api-key
5. Set Langfuse Observability Keys
In app.py (or at the top of your script), configure Langfuse:

python
Copy
Edit
LANGFUSE_PUBLIC_KEY = "your-langfuse-public-key"
LANGFUSE_SECRET_KEY = "your-langfuse-secret-key"
These are encoded into Basic Auth and sent to Langfuse’s EU server for telemetry:

python
Copy
Edit
os.environ["OTEL_EXPORTER_OTLP_ENDPOINT"] = "https://cloud.langfuse.com/api/public/otel"
os.environ["OTEL_EXPORTER_OTLP_HEADERS"] = f"Authorization=Basic {LANGFUSE_AUTH}"
👨‍💼 Agents
🕵️ Market Research Analyst
Role: Analyze latest AI trends

Tools:

SerperDevTool – search real-time info

WebsiteSearchTool – extract key details from pages

✍️ Content Writer
Role: Write blog posts in markdown

Tools:

DirectoryReadTool – reads past blog posts

FileReadTool – reads individual files

📋 Task Flow
Task 1 – Market Research
The Analyst agent uses search tools to find top 3 AI trends and summarizes them.
Output includes images and unique insights.

Task 2 – Blog Writing
The Writer uses the summary and past blog style to create a 4-paragraph markdown post.

Final output is saved as:

bash
Copy
Edit
blog-posts/new_post.md
💡 Sample Blog Output
markdown
Copy
Edit
# 3 Cutting-Edge Trends in AI (2025)

The AI landscape is evolving rapidly...

1. **Self-healing Neural Networks**...
2. **AI-Powered Robotics in Surgery**...
3. **Synthetic Data for Model Training**...

![AI Trend Chart](https://example.com/chart.png)
🔬 Observability & Tracing
Langfuse captures agent workflows, task execution, and errors

OpenLit gives lightweight, low-overhead tracing

You can visit https://cloud.langfuse.com to view full trace logs.

🧪 To Run
bash
Copy
Edit
python app.py
Watch your agents research and write autonomously, saving the final post to blog-posts/new_post.md.

🔒 .gitignore
Add the following to protect your secrets:

gitignore
Copy
Edit
.env
__pycache__/
*.pyc
*.log
🧠 Future Ideas
Add fact-checking or citation agents

Integrate Grammarly or AI copy-editing

Schedule automatic publishing to WordPress or Medium

Add multi-language blog generation

👩‍💻 Author
Dania Amin Khan

📄 License
MIT License. Use freely, just give credit.
