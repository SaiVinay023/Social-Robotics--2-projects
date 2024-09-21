
---

# Navigation Assignment: Programming Pepper and NAO Robots

## Project Name: Navigation Assignment

### Project Description

This project focuses on developing and simulating navigation behaviors for Pepper and NAO humanoid robots using Promela and the Aldebaran Robotics environment. The primary goal is to create interactive and social behaviors for the robots, enabling them to engage with humans in a natural and conversational way. The assignment explores how Pepper and NAO can navigate their environment, handle conversations, and demonstrate human-like expressions (such as "Confused" or "Thinking") in response to different stimuli.

The project is structured into multiple conversational states where the robots interact with users through predefined behaviors and dialogue systems.

### Project Details

- **Robots**: Pepper, NAO
- **Languages/Frameworks**: 
  - **Promela**: For modeling and verification of robot behaviors.
  - **Aldebaran Choregraphe**: Used to define robot behaviors, conversations, and animations.
- **Assignment Goal**: Enable Pepper and NAO to navigate and engage in conversations, showing social cues based on their state ("Thinking", "Confused", etc.).

The project contains various behavior `.xar` files, which define how Pepper or NAO responds to different conversational triggers, along with dialogue and translation files that handle multiple language interactions.

---

## Project Structure

```
├── behavior_1                  # Main folder containing behavior scripts for Pepper or NAO
│   ├── behavior.xar            # Behavior definition file for robot interactions
│   ├── translations            # Language translation files for multiple languages
│   │   ├── translation_en_US.ts # Translation for English (US)
│   └── manifest.xml            # Manifest file for behavior description
├── Confused                    # Folder defining the 'Confused' state
│   ├── Confused.dlg            # Dialogue for 'Confused' state
│   ├── Confused_enu.top        # Top-level dialogue configuration
├── Thinking                    # Folder defining the 'Thinking' state
│   ├── Thinking.dlg            # Dialogue for 'Thinking' state
│   ├── Thinking_enu.top        # Top-level dialogue configuration
├── conversation                # Main conversation configuration
│   ├── conversation.dlg        # Core dialogue configuration
│   ├── conversation_enu.top    # Top-level dialogue configuration
├── S4845876.pml                # Promela code for behavior verification
├── Navigation assignment.pml   # Promela code for navigation simulation
├── Assignment_3.xlsx           # Additional assignment documentation
├── Social Robotics questionarie.pdf  # Social robotics questionnaire for project context
└── Social robotics(responses).xlsx  # Survey results for project analysis
```

---

## Technical Implementation

### Behavior Design

1. **Behavior Definition**: 
   The `.xar` files (e.g., `behavior.xar`) define different robot behaviors in response to specific conversational inputs. For example, in the "Confused" state, Pepper or NAO will exhibit puzzled body language and engage in a corresponding conversation.
   
   **Key File**: `behavior.xar`
   
   **Example**: 
   - When a user asks a difficult question, the robot enters the "Confused" state and asks for clarification. This is defined in the `Confused.dlg` file, which maps out the conversation flow.

2. **Conversation Flow**:
   The robot's conversations are pre-programmed in `.dlg` files such as `conversation.dlg` and are triggered by dialogue tree structures (`conversation_enu.top`). These dialogues control the back-and-forth interactions between the user and the robot. They also determine transitions between robot behaviors like "Thinking" and "Confused."

   **Key File**: `conversation.dlg`
   
   **Example**: 
   - When the robot is "Thinking" about a response, the dialogue is handled by the `Thinking.dlg` file, where appropriate answers or follow-up questions are mapped.

3. **Promela for Verification**:
   Promela (Process Meta Language) is used for behavior modeling and verification. The `.pml` files simulate robot behavior in response to navigation commands or conversational cues. This helps verify if the robot will behave correctly in various scenarios.

   **Key File**: `Navigation assignment.pml` and `S4845876.pml`
   
   **Example**: 
   - The `Navigation assignment.pml` file might simulate the robot’s pathfinding behavior as it navigates through a room while interacting with users.
   
4. **Translation and Localization**:
   The project includes translation files to support multilingual conversations, allowing the robots to interact with users in different languages. This is managed by the `.ts` translation files (e.g., `translation_en_US.ts`).

---

### Example Implementation

Here’s an example of how robot behavior is defined and executed:

#### 1. Behavior Implementation (Confused)

- **File**: `Confused.dlg`
  
```plaintext
Robot: "I'm sorry, I'm a bit confused. Could you clarify that for me?"
User: Provides clarification.
Robot: "Ah, I see! Thanks for clearing that up."
```

#### 2. Behavior Verification Using Promela

- **File**: `Navigation assignment.pml`

```promela
init {
    bool isConfused = false;
    bool isThinking = false;

    if
    :: (user_asks_question) -> isConfused = true;
    :: (clarification_given) -> isConfused = false; isThinking = true;
    fi;
}
```

#### 3. Conversation Flow (Thinking)

- **File**: `Thinking.dlg`

```plaintext
Robot: "Let me think for a moment..."
Robot pauses, simulates thinking.
Robot: "Alright, here's my response."
```

---

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/YourUsername/Navigation-Assignment.git
   ```

2. Install **Choregraphe** (if you are using Pepper or NAO SDK).
   - Download from the [SoftBank Robotics Developer Center](https://developer.softbankrobotics.com/).

3. Open the `behavior_1/behavior.xar` file in **Choregraphe** to visualize and modify the robot behavior.

4. To run the behavior simulation:
   - Load the `.xar` files into Pepper/NAO using the SDK.
   - Alternatively, run the `.pml` files using a Promela simulator for verification.

---

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

This `README.md` covers the project name, description, structure, and technical implementation. It is written to guide users through the various components of the project and help them understand the behavior modeling and verification done using Promela for Pepper and NAO robots.
