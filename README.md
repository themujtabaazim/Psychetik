# Let’s leverage technology for good.

An application that not only helps identify those suffering from poor mental health but also provides support and care; as this technology is currently absent, to help others come out to talk about their mental health and seek support without the hesitation and fear of being judged by people, as well as in recent conditions of social distancing and lockdowns preventing people from going outside their homes.

This technology is new, and not many alternatives exist, besides manual work. The absence of a practicing mental health specialist as well as the hesitation of people is one of the challenges yet faced.

I believe almost all of us have had the experience of interacting with a chatbot. Sometimes we could immediately know that it’s a bot, but sometimes we couldn’t since it replied to our messages in a very natural way.

Without wasting any more time, let’s take a deep breath, grab a cup of coffee, and I will guide you on how to build a chatbot easily with the RASA framework!

Why RASA?

Popular examples of chatbots include SIRI by Apple, Alexa by Amazon, IBM Watson Assistant, and Google assistant. Chatbots are run by conversational AI-based algorithms. These chatbots use techniques like natural language processing and natural language generation to be able to understand and respond to commands by users in a natural conversation language used by humans instead of a typical software dependant drop-down or option selection menu. These days chatbots are getting better and better at understanding natural conversational language, sentiment analysis, command execution, and responding in a more human and empathic way. The main function or purpose of a chatbot is to talk to humans in a natural conversational manner and a) either give relevant advice b) give relevant answers/info or c) execute a command or action as ordered by the human to the bot. Most chatbots today will be doing one of the 3 things. While popular chatbots like Alexa and Google assistant are to give general search info or execute commands that run your household or security appliances, medical chatbots are something entirely different and hold a very significant and important role in the coming decade.

Rasa is an open-source machine learning framework used in building contextual AI assistants and chatbots in text and voice. It is a robust platform that includes natural language understanding and open-source natural language processing. It’s a full toolset for extracting the important keywords, or entities, from user messages, as well as the meaning or intent behind those messages. Rasa NLU (Natural Language Understanding) is a tool for understanding what is being said in short pieces of text; it also happens to be my favorite chatbot platform for several reasons, such as it being open-sourced, widely used, and well documented.

Overcoming problems of Social stigma and taboos: Many ailments are sort of embarrassing and difficult to discuss for patients. Patients, especially teenagers, and young adults find it hard to share problems relating to sexual health or mental health issues. They ignore these problems and sometimes avoid seeking help out of fear of insult or finding out something bad may come up. 70% of the mental health problems also begun during childhood or adolescence, and youth experiencing the highest rates than any other age group. The reason that this is such a big problem is that mental illness can reduce life expectancy by 10–20 years.

    Chatbots are a more personal and private advising system. A chatbot will never judge you and will guide in an empathetic and personal way to seek timely help and guidance.

Hence chatbots can overcome challenges that are not tackled because of social stigma and taboos.

A Medical Chatbot is one that can take in user’s messages about their health issues and respond accordingly to either provide answers, info, or other needed advice as well as execute such related commands like booking appointments or reminding on medication compliance.

RASA Installation and Setup

Step 1- Install RASA

    Download Anaconda Prompt from here.
    Download Microsoft build tools here.
    Create a directory on your system where you would like to store your Rasa project.

Once all of that has been done, open the Anaconda Prompt application and ‘cd’ into the directory you created, mine is called ‘RasaBot’.

    Create a virtual environment using the command below.

conda create -n rasavirtualenv python=3.6

2. Activate your environment using the command

conda activate rasavirtualenv

3. Install Rasa Open Source.

pip install rasa

Step 2: Setup a base project

    rasa init: command creates a new Rasa project in a local directory, which you will specify by providing the directory name.

Rasa will automatically populate it with the project files and example training data, and it will train the NLU and dialogue models. By default, rasa init trains a simple assistant called moodbot which will ask how you feel, and if you are unhappy it will try to cheer you up by sending you a picture of a cute tiger cub.

RASA Deep Learning Framework

The framework has these modules :

    Rasa NLU: Handles the Natural Language Processing
    Rasa NLU is like the “ear” of your assistant — it helps your assistant understand what’s being said. Rasa NLU takes user input in the form of unstructured human language and extracts structured data in the form of intents and entities.
    RASA Core: Handles data storing, piping, API, and basically the Assistant

Rasa framework is split into Rasa NLU and Rasa Core python libraries. The first one is the natural language understanding module used for intent classification and entity extraction with the aim to teach the chatbot how to understand user inputs based on machine learning. With Rasa Core, you teach the chatbot how to make responses by training dialogue management set up on deep learning. At this point, Rasa Core is used to teach the chatbot how to make responses using a deep learning model: LSTM neural network implemented in Keras. When user input is coming it is passed to the interpreter (Rasa NLU) with the goal to extract intents, entities, and other structured information. The next steps are managed by Rasa Core. The tracker is used to store the conversation history in memory, it maintains the conversation state. The policy decides what action to take at every step in the dialogue. It is generated along with a featurizer, which creates a vector representation of the current dialogue state given by the tracker. In the end, action is executed sending a message to the user and passing a tracker instance.

RASA Components

    __init__.py : Initiates the directory containing the packages required for running the chatbot.
    endpoints.yml: This contains the different endpoints the chatbot can utilize. One of the important endpoints is action_endpoint which exposes the chatbot to the Custom Action server and the UI.
    domain.yml: Defines the boundaries (environment) of the chatbot and the guidelines on how the chatbot should function. Some key aspects of the domain file are entity, intents, responses, actions, slots, session_config.
    Entities are keywords used to identify and extract useful data from inputs, like users’ names. For example, the message ‘My name is Juste’ has the name ‘Juste’ in it. An assistant should extract the name and remember it throughout the conversation to keep the interaction natural. Entity extraction is achieved by training a named entity recognition model to identify and extract the entities (in this example, names) for unstructured user messages.
    Utterance templates ‘utter_’ are the messages the bot will send back to the user. In templates, there are messages linked to the actions of the bot.
    Slots represent the bot’s memory, they store key values gathered by the user or by the outside world.
    credentials.yml: As the name suggests, this file is used to store the details (credentials) of various connected services.
    config.yml: This file contains the configuration we set up for our NLU and Core models. Policies, pipelines, etc are defined here.
    actions.py: This file contains the main logic of the chatbot. Actions define the responses of the chatbot.
    Actions are the things your bot runs in response to user input. There are three kinds of actions in Rasa Core:
    i. default actions (action_listen, action_restart, action_default_fallback)
    ii. utter actions, starting with utter_, which just sends a message to the user.
    iii. custom actions — any other action, these actions can run arbitrary code
    models: This folder stores the trained models.
    data: this is the brain of the chatbot. The context, learning, and improvement help with the files existing in the data folder. What are those files, you ask? They are nlu.md and stories.md
    nlu.md: This file contains the training data. Natural Language Understanding is the name given by RASA which helps turn User Messages into structured data. Basically, these are the samples (and examples) which we can expect the user may input. The NLU training data also labels the entities, or important keywords, the assistant should extract from the example utterance. In each intent, are defined examples of user utterances, entities, and how to respond. Basically, intents are labels that represent the goal or meaning, of a user’s specific input. For example, the message ‘Hello’ could have the label ‘greet’ because the meaning of this message is a greeting. If you have ever developed a Conversational AI agent using NLU, you know how often users don’t follow the happy path. They may say or type responses that make perfect sense however their responses still fall outside of any intent.
    nlu.md basically consists of intent examples ie user input
    stories.md: This file contains the conversational flow of the chatbot and the user, which we have defined (trained). Stories are examples of end-to-end conversations. These are important in deciding the next action of the chatbot. Dialogue Management can be the term used to loosely define stories.md.
    Stories are basically dialog flow of the chatbot

**Note- Check out the linked words to be redirected to the files in the GitHub Repository for the mental health chatbot developed in Rasa

By default, Rasa NLU comes with a bunch of pre-built components (and even fully designed pipelines) to use:

Intro to Custom Components

Using the pre-built Rasa NLU components, users and developers have a lot of freedom in customizing the models. However, in some situations, one might want to add a component that is not natively implemented in Rasa NLU. For example, developers could add a sentiment analyzer that will enable their assistant to use different responses depending on the user’s mood.

How to run custom actions?

In the RASA stack, you can write custom actions in actions.py. After writing custom actions, you can't use those in stories without starting actions webhook. Of course, you can use those actions, but it won't work as you expect since you haven't started your webhook.

How to train your RASA bot?

After you add entities, intents, actions, and stories, you need to run your bot and see whether it works or not. But you can’t just run your bot and see results just like that when you add some new data. After you add anything to endpoints.yml, nlu.md, or stories.md files, you need to train your bot for the newly added data. You can train your bot by typing rasa train and your model related to your bot will be trained.

How to run your RASA bot?

Now that you have trained your bot, you can run your bot and you can start a good conversation with it. rasa shell command run your bot and prompt a window to chat with your bot. After you run your bot, you can stop it by typing /stop command as your bot input.
#
