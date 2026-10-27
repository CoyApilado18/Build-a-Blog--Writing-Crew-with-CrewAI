<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Build a Blog Writing Crew with CrewAI

**Project Link:** [View Project](https://nextwork.ai/projects/99b558af-381c-5c9e-afef-a2d5e19992c0)

**Author:** Emmanuel Apilado  
**Email:** apilado.emmanuel18@gmail.com

---

![Image](https://nextwork.ai/thankful_indigo_wise_blackberry/uploads/99b558af-381c-5c9e-afef-a2d5e19992c0_h6t9b3y7)

## Introducing Today's Project!

You have probably used AI chatbots to help you write before, but what if instead of one AI doing everything, you could build a whole team of AI specialists that each handle a different part of the job?  

In this project, I will build a multi-agent system using CrewAI where three AI agents (a Researcher, a Writer, and an Editor) collaborate in a sequential workflow to produce a polished blog post on any topic you choose.  

I'm interested in this because this will help me build my own multi-agent system in my future projects as a DevOps Practitioner.  

### Key tools and concepts

The key tools and concepts I used includes:
- Python 3.12+ as the programming language
- [CrewAI](https://docs.crewai.com/v1.15.30/en/introduction) as the Python Framework 
- [gemini-3.5-flash-lite](https://docs.cloud.google.com/gemini-enterprise-agent-platform/models/gemini/3-5-flash-lite) as the AI model
- [uv](https://pydevtools.com/handbook/reference/uv/) as a package manager
- [Google AI Studio](https://aistudio.google.com/api-keys) to generate API key to use the Gemini model.

### Challenges and wins

This project took me approximately half a day in a way that I also learned the code playout, structure, concept moreso how everything is wired and blends together. The most challenging part was really just distractions as it interrupts my train of thought as I'm building and studying at the same time and troubleshooting some part -that's it only. Other than that, finishing the project felt there's a sense of achivement and the learning is a abig win.

### Personal reflection

I did this project today to learn how to use CrewAi its concept along with other tools needed to build for this project. Another skill I want to learn is how to utilize RAG or MCP.

## Installing Python and CrewAI

In this step, I will install Python, a package manager called uv and the CrewAI CLI. Then grab free API key from Google to use Gemini as the brain behind our agents. 

![Image](https://nextwork.ai/thankful_indigo_wise_blackberry/uploads/99b558af-381c-5c9e-afef-a2d5e19992c0_v8bn4x1w)

### Understanding the uv package manager

I learned that uv is a fast python package manager built in Rust. I replaces older tools like pip and virtualenv with a single, much faster tool. CrewAI uses uv under the hood to manage our projects dependecies and virtual environment.


## Scaffolding the CrewAI Project

In this step, we'll need a project structure for our blog writing crew. We'll:
- Create a new CrewAI project using the CLI.
- Explore the project structure.
- Configure our API key and model settings. 



![Image](https://nextwork.ai/thankful_indigo_wise_blackberry/uploads/99b558af-381c-5c9e-afef-a2d5e19992c0_v4nt8wf6)

### Key project files

Two key files are: 
`agents.yaml` which defines who (their roles) the agents are and, 
`tasks.yaml` which defines each agents tasks or what they will do. 

![Image](https://nextwork.ai/thankful_indigo_wise_blackberry/uploads/99b558af-381c-5c9e-afef-a2d5e19992c0_w2dc5nq8)

## Configuring AI Agents

In this step, I'm going to define our agents by configuring each agent with their roles, goals and backstory in the `agent.yaml` file. 

![Image](https://nextwork.ai/thankful_indigo_wise_blackberry/uploads/99b558af-381c-5c9e-afef-a2d5e19992c0_j3x8n1v6)

### How agent configuration shapes AI behavior

The role is the job title of each agent, the goal is what they need to aim for the outcome and the backststory gives them a persona and expertise to draw fromwhen generating responses. 

## Defining the Task Pipeline

In this step, I'm defining the tasks for each agent in `tasks.yaml`. These tasks are important because these are set of instructions that I will configure for the agents respectively chaining them together:
1. Research the topic
2. Write a blog post.
3. Edit and polish the final draft


![Image](https://nextwork.ai/thankful_indigo_wise_blackberry/uploads/99b558af-381c-5c9e-afef-a2d5e19992c0_p3n8v5w1)

### How the tasks chain together

The tasks are chain together by passing the result of the first task (a research brief) by the Researcher agent on to the second task to turn that brief into a blog post by the Writer agent and finally polished the blog post by the Editor agent for the final post and saves it to output/blog_post.md file. Only the Editor agent has the output_file field as the last task needs this because the earlier outputs are passed directly to the next agent in memory.

## Connecting YAML Configuration to Python

I'm connecting the 3 agents defined in the `agents.yaml` and 3 tasks defined in `tasks.yaml` and turn it into a "working crew" using a Python file named `crew.py`. This will tell the CrewAI framework to read those configurations and create the actual objects and run them.

![Image](https://nextwork.ai/thankful_indigo_wise_blackberry/uploads/99b558af-381c-5c9e-afef-a2d5e19992c0_p3n8v2q6)

### Why method names must match YAML keys

The method names in `crew.py` need to match the keys in my YAML files because these methods creates a Python object from my YAML files. It pulls the keys (researcher, writer, editor) from the YAML file when creating a Python object (an Agent object) that is why the method names should match the keys in my YAML file.

![Image](https://nextwork.ai/thankful_indigo_wise_blackberry/uploads/99b558af-381c-5c9e-afef-a2d5e19992c0_h8f4d6a2)

## Running the Blog Writing Crew

In this step, I'll verify CrewAI framework knows how to talk to Google Gemini as this is the language model we selected. I'll also install all the project dependencies that CrewAI scaffolded project requires. We'll:
- Install dependencies and run our crew.
- Watch your agents collaborate to produce a blog post.
- Experiment with a different topic.

![Image](https://nextwork.ai/thankful_indigo_wise_blackberry/uploads/99b558af-381c-5c9e-afef-a2d5e19992c0_p4n8v1q6)

### How the agents collaborated

I ran my crew and the agents collaborated sequentially by passing the result/output from the researcher -> writer -> editor agents and perform their tasks from the given output. 

![Image](https://nextwork.ai/thankful_indigo_wise_blackberry/uploads/99b558af-381c-5c9e-afef-a2d5e19992c0_h6t9b3y7)

## Adding a Social Media Manager Agent

In this project extension, I'm adding a fourth agent, a Social Media Manager agent to  that turns polished blog posts into Twitter/X threads and LinkedIn posts where this will simulate how companies use multi-agent AI systems to automate content. 

![Image](https://nextwork.ai/thankful_indigo_wise_blackberry/uploads/99b558af-381c-5c9e-afef-a2d5e19992c0_w3f8j1v6)

### Extending the crew with new agents and tasks

I added the social media manager by creating Social Media Manager agent in agents.yaml, then added a task for the Social Media Manager agent in tasks.yaml, and finally added the wiring for this agent in crew.py.

![Image](https://nextwork.ai/thankful_indigo_wise_blackberry/uploads/99b558af-381c-5c9e-afef-a2d5e19992c0_t6c1g4q8)

### Social media output

In this project extension, my social media agent generated a posts where it clearly outlined social media contents for Twitter thread and the LinkedIn Post Summary. It differs from the original blog posts as the structure of the original post is more of a "blog" concept where the Social Media Manager agent uses that polished blog to create a socia media content for the Twitter/X and LinkedIn social media platforms where it highlights key points and created a summary of the main takeaways in a professional tone. 

### Experimenting with agent backstories

When I changed the backstory of the Social Media Manager to its defined persona, the tone of the output changed. ... This showed me that the difference in tone shows how much the backstory influences our agent's output. This is a powerful way to customize agent behavior without changing any code.

---

*Built with [NextWork](https://nextwork.ai) - [View this project](https://nextwork.ai/projects/99b558af-381c-5c9e-afef-a2d5e19992c0)*
