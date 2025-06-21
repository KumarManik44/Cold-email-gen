###📧 Cold Email Generator
An end-to-end LLM-powered tool that helps Software and AI services companies generate personalized cold emails for potential clients by analyzing job postings and matching them with company portfolios.
🚀 Features

Web Scraping: Extracts job postings from career pages
AI-Powered Analysis: Uses Llama 3.1 to analyze job requirements
Smart Matching: Matches job skills with company portfolio using vector similarity
Personalized Emails: Generates tailored cold emails with relevant portfolio links
Interactive UI: Built with Streamlit for easy use

🛠️ Tech Stack

LLM: Llama 3.1 (via Groq API)
Vector Database: ChromaDB
Framework: LangChain
Frontend: Streamlit
Data Processing: Pandas
Web Scraping: LangChain WebBaseLoader

📁 Project Structure
cold-email-generator/
├── app/
│   ├── resource/
│   │   └── my_portfolio.csv
│   ├── chains.py
│   ├── portfolio.py
│   ├── utils.py
│   └── main.py
├── notebooks/
│   └── Cold Email Generator.ipynb
├── vectorstore/
├── .env
├── .gitignore
├── requirements.txt
└── README.md
🔧 Installation

Clone the repository
bashgit clone https://github.com/yourusername/cold-email-generator.git
cd cold-email-generator

Create a virtual environment
bashpython -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

Install dependencies
bashpip install -r requirements.txt

Set up environment variables
Create a .env file in the root directory:
envGROQ_API_KEY=your_groq_api_key_here

Prepare your portfolio data
Update app/resource/my_portfolio.csv with your company's portfolio information:
csvTechstack,Links
"React, Node.js, MongoDB",https://example.com/react-portfolio
"Python, Django, MySQL",https://example.com/python-portfolio


🚀 Usage

Start the Streamlit app
bashstreamlit run app/main.py

Open your browser and navigate to http://localhost:8501
Enter a job posting URL (e.g., from company career pages)
Click Submit to generate personalized cold emails

📊 How It Works

Web Scraping: The tool scrapes job posting content from the provided URL
Job Extraction: Llama 3.1 extracts key information (role, experience, skills, description)
Portfolio Matching: ChromaDB finds relevant portfolio items based on job skills
Email Generation: AI generates a personalized cold email highlighting relevant capabilities

🔑 Key Components
chains.py

Handles LLM interactions
Extracts job information from scraped content
Generates personalized cold emails

portfolio.py

Manages portfolio data and vector database
Performs similarity search for relevant projects
Loads and queries ChromaDB collection

utils.py

Text cleaning and preprocessing utilities
Removes HTML tags, URLs, and special characters

main.py

Streamlit web application
User interface and workflow orchestration

📝 Example Usage
pythonfrom chains import Chain
from portfolio import Portfolio

# Initialize components
chain = Chain()
portfolio = Portfolio()

# Load portfolio data
portfolio.load_portfolio()

# Extract job information
jobs = chain.extract_jobs(cleaned_job_text)

# Generate cold email
for job in jobs:
    skills = job.get('skills', [])
    links = portfolio.query_links(skills)
    email = chain.write_mail(job, links)
    print(email)
🔒 Environment Variables

GROQ_API_KEY: Your Groq API key for accessing Llama 3.1

📋 Requirements

Python 3.8+
Groq API key
Internet connection for web scraping

🤝 Contributing

Fork the repository
Create a feature branch (git checkout -b feature/amazing-feature)
Commit your changes (git commit -m 'Add amazing feature')
Push to the branch (git push origin feature/amazing-feature)
Open a Pull Request

📄 License
This project is licensed under the MIT License - see the LICENSE file for details.
🙏 Acknowledgments

Groq for providing fast LLM inference
LangChain for the excellent framework
ChromaDB for vector storage capabilities
Streamlit for the intuitive UI framework

🔮 Future Enhancements

 Support for multiple job posting formats
 Email template customization
 Batch processing capabilities
 Integration with email clients
 Advanced analytics and tracking
 Multi-language support
