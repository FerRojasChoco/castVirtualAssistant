# NOTE: This repository is made public only from time to time to allow companies interested in my profile as a developer. 
## It will be closed again after 1~2 weeks. The contents of the project have been modified before uploading it as a github repository to maintain confidentiality on the company's information.
## 🚀 CAST Virtual Assistant

This is a virtual assistant designed for Cast S.A. (IT Company based in Paraguay), built using the **Rasa** framework.

-----

### Project Overview 

This project implements a conversational AI assistant to answer common customer inquiries about Cast's services, location, operating hours, app download links, and user creation process. The assistant is built in **Spanish** (`language: es`).

### Technology Stack

The assistant is developed using **Rasa**, an open-source platform for creating virtual assistants at scale. Rasa offers extensive customization and privacy compared to other options.

The core components used are:

  * **Rasa NLU:** For Natural Language Understanding (identifying user intents).
  * **Rasa Core:** For dialogue management (determining the assistant's next action).

### Assistant Capabilities (Intents & Responses)

These are some of the  intents and corresponding bot responses are configured in `domain.yml`:

| Intent | Description | Bot Response (`utter_...`) |
| :--- | :--- | :--- |
| `greet` | User says hello. | `utter_greet` (e.g., "Hola\! En que te puedo ayudar?") |
| `goodbye` | User says goodbye. | `utter_goodbye` (e.g., "Hasta luego\!") |
| `thanks` | User thanks the bot. | `utter_thanks` (e.g., "Cast se complace de servirle\!") |
| `bot_challenge` | User asks if the bot is a human/bot. | `utter_iamabot` (e.g., "Soy un robot, hecho en Rasa.") |
| `ask_location` | User asks for the office address. | `utter_ask_location` (Provides address and map link) |
| `ask_prices` | User asks about service costs. | `utter_ask_prices` (Refers user to a commercial advisor) |
| `ask_services` | User asks about available services. | `utter_ask_services` (Lists example services like preparing forms and supervising collaborators) |
| `ask_hours` | User asks for operating hours. | `utter_ask_hours` (Provides hours (L-V 8:00-17:30, S 8:00-12:00) and support/admin/commercial contact numbers) |
| `ask_app_download`| User asks how to download the app. | `utter_ask_app_download` (Provides links for "Viejo Mobile" and "Nuevo Mobile" apps) |
| `ask_create_user`| User asks how to create a user. | `utter_ask_create_user` (Provides step-by-step instructions and suggests next steps with buttons for "Usuario Movil" and "Usuario Web") |
| `affirm` | User affirms a statement. | |
| `deny` | User denies a statement. | |
| `mood_great` | User expresses positive mood. | |
| `mood_unhappy`| User expresses negative mood. | |

### 📂 Project Structure

  * **`domain.yml`**: Defines the intents, responses (`utter_...`), actions, and the session configuration.
  * **`nlu.yml`**: Contains training examples for the Natural Language Understanding model, mapping user phrases to their respective intents.
  * **`stories.yml`**: Defines typical conversational flows (stories) between the user and the assistant.
      * *Example Story:* `user asks about time` -\> `intent: ask_hours` -\> `action: utter_ask_hours`.
  * **`rules.yml`**: Defines simple, fixed conversational paths (rules) for intents like `greet`, `goodbye`, `thanks`, and `bot_challenge`.
  * **`config.yml`**: Contains the NLU and Core pipeline configuration. The language is set to Spanish (`es`).
  * **`credentials.yml`**: Stores credentials for connecting to messaging channels (currently configured for `rest` channel).
  * **`endpoints.yml`**: Defines external endpoints for custom actions, model storage, and event brokers.

### Basic flow to follow for running the model (check RASA documentation for more information)

1.  **Install Rasa:** Ensure you have the Rasa framework installed.
    ```bash
    pip install rasa
    ```
2.  **Load the Project:** Place all configuration files in a Rasa project directory.
3.  **Train the Model:** Train the conversational model using the provided configuration.
    ```bash
    rasa train
    ```
4.  **Run the Assistant:** Start the server to interact with the assistant on the command line.
    ```bash
    rasa shell
    ```
