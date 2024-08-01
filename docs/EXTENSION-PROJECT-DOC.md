## OpenGPTs RAG Bot Evaluation with G-Eval: Design Document

### 1. Project Goal

This project aims to extend the OpenGPTs UI to facilitate the evaluation of RAG Bots using the G-Eval framework. Users will be able to define custom evaluation criteria, provide questions and expected answers, and obtain a comprehensive evaluation score for their RAG Bot's performance.

### 2. System Design

#### 2.1 Frontend UI Extension

- **G-Eval Configuration Panel:**
    - A new panel in the OpenGPTs UI, accessible when creating or editing a RAG Bot, dedicated to configuring G-Eval parameters.
    - Fields for:
        - **Metric Name:** Descriptive name for the evaluation metric (e.g., "Factual Accuracy").
        - **Evaluation Criteria:** Free-text description of the evaluation aspects (e.g., "Assess factual correctness based on the context provided.").
        - **Evaluation Steps (optional):** A list of explicit steps the LLM should follow during evaluation. If not provided, G-Eval will generate steps based on the criteria.
        - **Threshold (optional):** Minimum score (0-1) for a test case to pass, defaults to 0.5.
        - **LLM Model (optional):** Selection from available LLM models, defaults to the RAG Bot's LLM.
        - **Strict Mode (optional):** Checkbox to enable binary scoring (1 for perfect, 0 otherwise) and override threshold to 1.
        - **Verbose Mode (optional):** Checkbox to print intermediate evaluation steps to the console.

- **Test Case Definition:**
    - A section within the panel to define multiple test cases.
    - Each test case will include:
        - **Question:** The question to be posed to the RAG Bot.
        - **Expected Answer:** The ideal answer based on the provided context.
        - **Context (optional):** Additional context relevant to the question.
        - **Additional Inputs (optional):** Any other input parameters relevant to the evaluation criteria (as defined in G-Eval).

- **Evaluation Results Display:**
    - Upon running the evaluation, a new section will display the results.
    - It will show:
        - Overall evaluation score (0-1) for the entire set of test cases.
        - Individual scores and reasons for each test case.
        - Option to toggle verbose mode to view intermediate steps.

#### 2.2 Backend Integration

- **API Endpoints:**
    - New endpoints to:
        - Save G-Eval configurations associated with a RAG Bot.
        - Retrieve G-Eval configurations for a RAG Bot.
        - Trigger evaluation execution.
        - Fetch evaluation results.

- **G-Eval Execution:**
    - Utilize the `deepeval` library to instantiate and execute G-Eval metrics.
    - Leverage existing LangChain infrastructure to:
        - Run the RAG Bot on each test case question.
        - Use the selected LLM model to evaluate the RAG Bot's output based on the defined criteria, steps, and additional inputs.

- **Data Storage:**
    - Store G-Eval configurations in the database linked to the corresponding RAG Bot.
    - Store evaluation results, including individual scores and reasons, in the database linked to the evaluation run.

### 3. Workflow

1. **Configuration:** The user creates a RAG Bot using OpenGPTs UI and defines the G-Eval parameters and test cases.
2. **Storage:** The backend saves the G-Eval configuration to the database.
3. **Evaluation Trigger:** The user triggers the evaluation process from the UI.
4. **Run Execution:** The backend runs the RAG Bot on each test case question, capturing the actual output.
5. **G-Eval Measurement:** The backend uses the selected LLM model and the G-Eval configuration to evaluate each test case, generating a score and a reason.
6. **Results Storage:** The backend stores the evaluation results in the database.
7. **Results Display:** The frontend fetches and displays the results to the user.

### 4. Potential Issues and Considerations

- **Performance:** Running multiple evaluations with large LLMs can be computationally expensive. Consider implementing:
    - Asynchronous task processing to prevent blocking the UI.
    - Caching mechanisms for LLM responses and retrieval results.
- **User Interface Complexity:** The additional configuration options and test case definitions could make the UI more complex. Focus on intuitive design and clear documentation to ensure usability.
- **Evaluation Criteria Flexibility:** G-Eval's flexibility in defining evaluation criteria relies on natural language understanding. Thorough testing and clear instructions are crucial to ensure accurate and consistent evaluations.
- **Bias in LLM Evaluation:** The LLM used for G-Eval could introduce its own biases into the evaluation process. Carefully select the LLM model and be aware of its limitations.

### 5. Conclusion

Integrating G-Eval into OpenGPTs provides a powerful tool for developers to evaluate and improve their RAG Bots. By allowing customized evaluation criteria and detailed test case definitions, this project empowers users to assess their bots' performance with greater precision and flexibility, ultimately contributing to the development of more robust and effective RAG applications.

