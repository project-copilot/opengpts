Grooming Call Transcript

Participants: Matías (Project Manager), Sarah (Lead Developer), John (Backend Developer), Lisa (Frontend Developer), Michael (QA Engineer)

Matías: Hi team, thanks for joining the grooming call today. Our goal is to discuss the two new epics related to the extension project. We’ll be focusing on implementing G-Eval tests on OpenGPTs and creating two RAG bots, one using GPT-4 and the other using Claude 2. Let’s start with the first epic. Sarah, could you give us an overview?

Epic 1: Implement G-Eval Tests on OpenGPTs
Sarah: Sure, Matías. The first epic is about extending our OpenGPTs UI to support G-Eval tests. This involves creating a configuration panel where users can define custom evaluation criteria, input questions, and expected answers, and then obtain a comprehensive evaluation score for their RAG Bot's performance. Here are the user stories for this epic:

User Story 1.1: As a user, I want to access the G-Eval Configuration Panel from the main OpenGPTs UI, so I can start setting up my evaluation criteria.

John: For this story, we'll need to modify the UI to include a new panel. This panel should allow users to define custom evaluation criteria. We can use a form with fields for questions, expected answers, and criteria selection.

Lisa: I'll work on the frontend changes. We need to ensure the panel is intuitive and user-friendly. I'll also add tooltips to guide users through the setup process.

User Story 1.2: As a user, I want to input my evaluation criteria and save it, so I can reuse it for future evaluations.

John: This will require backend support to store the evaluation criteria. We can create a new endpoint to handle saving and retrieving these criteria.

Michael: We should also consider validation here. The criteria need to be checked for completeness before saving.

User Story 1.3: As a user, I want to run G-Eval tests using my criteria and view the evaluation results in a detailed report.

Lisa: The frontend will need to display the evaluation results in a clear and detailed manner. We can use charts and graphs to visualize the scores.

John: The backend will handle the actual evaluation using G-Eval. We’ll integrate this with our existing evaluation framework.

Matías: Great, that covers the first epic. Let’s move on to the second one. John, can you introduce the next epic?

Epic 2: Create RAG Bots Using GPT-4 and Claude 2
John: Absolutely. The second epic is about creating two RAG bots, one with GPT-4 and the other with Claude 2. These bots will be evaluated using the criteria defined in the first epic. Here are the user stories:

User Story 2.1: As a developer, I want to integrate GPT-4 into our RAG bot framework, so I can create a bot that uses the latest language model.

Sarah: We’ll need to update our existing RAG bot framework to support GPT-4. This involves modifying the model integration layer and ensuring compatibility with GPT-4’s API.

John: I’ll handle the backend integration. We’ll need to test the bot extensively to ensure it performs as expected.

User Story 2.2: As a developer, I want to integrate Claude 2 into our RAG bot framework, so I can create a bot that offers an alternative to GPT-4.

Sarah: Similar to GPT-4, we’ll need to update the framework to support Claude 2. This involves a different set of API integrations and possibly some modifications to our existing codebase.

John: I’ll take care of this integration as well. We should also plan for a set of comparative tests between the GPT-4 bot and the Claude 2 bot.

User Story 2.3: As a user, I want to evaluate both RAG bots using the G-Eval framework, so I can determine which performs better based on my criteria.

Lisa: The UI will need an option to select which bot to evaluate. We can add a dropdown menu or a similar selection tool.

Michael: We should ensure that the evaluation process is consistent and that we capture detailed logs for each test. This will help us analyze any discrepancies between the two models.

Matías: Excellent. That wraps up our discussion on the two epics. Let’s assign the tasks and set milestones for our next sprint. Thanks, everyone, for your input. Let's aim to deliver these features with high quality and on time.

End of Transcript