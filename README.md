
# Product Search: Database Q&A 👕

This Streamlit application enables users to interact with a MySQL database using natural language queries. It leverages LangChain, semantic similarity matching, and few-shot learning to generate accurate SQL queries and retrieve relevant answers.

---

## Features

- **Natural Language to SQL:** Converts user queries into SQL commands to extract relevant information from the database.
- **Few-Shot Learning:** Uses pre-defined examples and semantic similarity for intelligent prompt generation.
- **Semantic Search:** Embeds few-shot examples and selects the most relevant ones for generating queries.
- **MySQL Support:** Connects to a local MySQL database for real-time data retrieval.
- **Dynamic Results:** Provides SQL results and user-friendly answers to queries.

---

## Requirements

### Dependencies

The following Python packages are required:
- `streamlit`
- `langchain`
- `langchain-community`
- `SQLAlchemy`
- `pymysql`
- `python-dotenv`

Install them using pip:

```bash
pip install streamlit langchain langchain-community SQLAlchemy pymysql python-dotenv
```

---

## Setup and Usage

1. **Database Configuration:**
   - Update the database credentials in the `get_few_shot_db_chain` function:
     ```python
     db_user = "root"
     db_password = "admin"
     db_host = "localhost:3306"
     db_name = "atliq_tshirts"
     ```

2. **Run the Application:**
   Execute the Streamlit app:
   ```bash
   streamlit run main.py
   ```

3. **Ask Questions:**
   Enter your question in the input field, and the application will process your query, generate an SQL command, retrieve data from the database, and provide an answer.

---

## Code Breakdown

### `get_few_shot_db_chain()`
- Connects to the MySQL database using SQLAlchemy and creates a connection.
- Embeds pre-defined few-shot examples using the Mistral model.
- Uses `SemanticSimilarityExampleSelector` to select relevant examples based on the user's query.
- Constructs a dynamic SQL query prompt using LangChain's `FewShotPromptTemplate`.
- Generates an SQL query, executes it, and returns results.

### Few-Shot Examples
- Pre-defined examples (`few_shots`) are embedded for semantic similarity checks.
- Relevant examples are included in the prompt dynamically based on the user's query.

### Streamlit Frontend
- Displays a text input for the user to ask questions.
- Processes the query using the SQL database chain and displays the result.

---

## Customization

### Few-Shot Examples
- Add or modify the examples in `few_shots` to enhance the application's response accuracy.

### Database Connection
- Update the database credentials to connect to a different database or use environment variables for security.

### Prompt Configuration
- Modify the `mysql_prompt` string to adjust the behavior and constraints of the SQL query generation.

---

## Future Improvements
- Add support for multiple databases (e.g., PostgreSQL, SQLite).
- Introduce advanced error handling for invalid queries or database connection issues.
- Enable dynamic configuration of database credentials through environment variables or a configuration file.

---

## License

This project is released under the MIT License. Feel free to use, modify, and distribute the code.

---

## Credits

Developed using:
- [Streamlit](https://streamlit.io/)
- [LangChain](https://www.langchain.com/)
- [SQLAlchemy](https://www.sqlalchemy.org/)
