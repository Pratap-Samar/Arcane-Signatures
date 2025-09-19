# Arcane Signatures: A D&D Class Spell Core Analysis 🧙‍♂️✨

This project analyzes and visualizes the Dungeons & Dragons 5th Edition spellbook to reveal the unique "magical signature" of each character class. Using a "hub and spoke" network graph, it provides an interactive way to explore which schools of magic define a class and which spells are most exclusive to them.



## The Motivation

As a player of D&D games like Baldur's Gate 3, I often found myself wasting valuable spell slots on spells that felt unique but were actually common and available to many other classes. This project was born from a desire to solve that problem by creating a practical tool to visualize a class's spellbook. It helps identify which spells are truly exclusive and define a class's core identity, allowing for more strategic spell selection.

---
## Key Findings & Analysis
This project's "Arcane Signature" visualization offers a clear and practical analysis of the magical identity of any D&D class. By moving beyond simple lists and tables, we can instantly conclude a class's core magical strengths and most unique spells.

For any selected D&D Class, it shows:
* **Compositional Strengths:** Which schools of magic are most dominant for a class?
eg: The graph immediately reveals that the Bard's spellbook is heavily dominated by large clusters of **Enchantment** (green) and **Illusion** (white) spells. This visually confirms the Bard's role as a master of manipulation, charm, and deception.
<img width="857" height="544" alt="image" src="https://github.com/user-attachments/assets/f5049970-d9f1-4453-bf46-6e5c9752d745" />



* **Exclusive Spells:** Within these clusters, we can identify the largest nodes, representing the spells most unique to the Class. This allows a player to quickly distinguish between a common spell and a more defining, class-specific spell, helping them make more strategic choices about which spells to prepare.
<img width="1542" height="661" alt="image" src="https://github.com/user-attachments/assets/bd70ec57-4556-4a35-bf7a-3ddedd1eb9e1" />


* **Practical Gaming Insights:** For a player in a game like Baldur's Gate 3, this analysis is invaluable. It provides a clear visual guide to avoid wasting precious spell slots on spells that might feel powerful but are actually common magical tools, allowing the player to focus on the spells that truly define their character's unique abilities.

---
## Challenges and Solutions
This project involved several data processing and visualization challenges. The final "Arcane Signature" graph is the result of iteratively solving these problems.


* **Challenge: The "Hairball" Problem**
    The first attempt to connect every spell in a class's list to every other spell resulted in a dense, unreadable "hairball" graph that was both analytically useless and too complex for the browser to render.
    **Solution:** I re-architected the graph into a **"hub and spoke"** model. The class name became the central node, and spells were only connected if they belonged to the same school of magic. This dramatically reduced the number of edges and created clear, meaningful clusters.

* **Challenge: Visualizing Exclusivity**
    While the "hub and spoke" model was cleaner, it lost the crucial information about which spells were exclusive to a class. My initial "radial layout" attempted this but was also too cluttered to read.
    **Solution:** I combined the best of both models. I kept the clean "hub and spoke" layout and reintroduced the exclusivity data by mapping it to a different visual channel: the **size of each spell node**. Spells known by fewer classes now appear larger, making the class's most unique and defining magic instantly identifiable.

* **Challenge: Effective Layout**
    The default physics simulation was not sufficient to untangle the spell clusters.
    **Solution:** I implemented the **ForceAtlas2** physics algorithm, a more advanced solver better suited for network graphs. By tuning its parameters (like applying a repulsive gravity force), the school clusters were pushed apart into a clean, aesthetically pleasing, and easy-to-analyze layout.

---
## Tech Stack & Data Source
* **Language:** **Python**
* **Environment:** **Google Colab**
* **Data Manipulation:** The **`pandas`** library was used for loading and preparing the spell data.
* **Graph Analysis:** The **`networkx`** library was used to construct the graph's nodes and edges.
* **Interactive Visualization:** The **`pyvis`** library transformed the graph into an interactive HTML file, using the **ForceAtlas2** physics engine to improve the layout.
* **Data Source:** The project uses the **Dungeons & Dragons Spell Listing** dataset from Kaggle, which can be found here: [D&D Spells Dataset](https://www.kaggle.com/datasets/mrpantherson/dndspells).

---
## Project Key: Classes, Schools & Colors
This project analyzes the spells available to the following D&D 5e classes:
* **Classes:** Artificer, Bard, Cleric, Druid, Paladin, Ranger, Sorcerer, Warlock, and Wizard.

The spells in the visualization are colored according to their school of magic, based on the following key:
* **Abjuration:** `#00bfff` (Deep Sky Blue)
* **Conjuration:** `#ff69b4` (Hot Pink)
* **Divination:** `#ffd700` (Gold)
* **Enchantment:** `#006400` (Dark Green)
* **Evocation:** `#ff4500` (OrangeRed)
* **Illusion:** `#ffffff` (White)
* **Necromancy:** `#dc143c` (Crimson)
* **Transmutation:** `#9932cc` (Dark Orchid)

---
## How to Run
1.  **Set up the environment:** Open the `Arcane-signatures.ipynb` notebook in Google Colab.
2.  **Upload Data:** Upload the D&D spell dataset file (`dnd-spells.csv`).
3.  **Execute Cells:** Run the notebook cells to install libraries, load and prepare the data, and create the color map.
4.  **Enter Class Name:** When prompted, enter the name of the D&D class you wish to analyze (e.g., "Wizard", "Sorcerer", "Bard").
5.  **Download & View:** The script will generate a self-contained HTML file (e.g., `wizard.html`). Download this file from the Colab file browser and open it in your web browser to explore the interactive graph.

## Graphs for every class
### 1. Artificer
<img width="710" height="686" alt="image" src="https://github.com/user-attachments/assets/000208b1-6524-494b-a38e-a11c5770b4f4" />

### 2.  Bard
<img width="910" height="777" alt="image" src="https://github.com/user-attachments/assets/2355f56d-172c-4972-8980-0b08a04910e0" />

### 3. Cleric
<img width="766" height="735" alt="image" src="https://github.com/user-attachments/assets/6a4848c1-3258-4adc-8fe0-e12936585eeb" />


### 4. Druid
<img width="841" height="768" alt="image" src="https://github.com/user-attachments/assets/98fa7ffc-184b-44cc-a6ee-8b920d9564d5" />

### 5. Paladin
<img width="814" height="765" alt="image" src="https://github.com/user-attachments/assets/7a243e88-095f-4098-9df1-7d7e8b292334" />

### 6. Ranger
<img width="1083" height="740" alt="image" src="https://github.com/user-attachments/assets/f39a2f1d-cc55-4279-8229-dc1b270efc98" />

### 7. Sorcerer
<img width="838" height="751" alt="image" src="https://github.com/user-attachments/assets/74efccc7-ba5b-45a3-a1eb-bf8579950ef9" />

### 8. Warlock
<img width="839" height="779" alt="image" src="https://github.com/user-attachments/assets/3e734391-ca7f-4445-b166-feb65b2b6df5" />

### 9. Wizard
<img width="889" height="727" alt="image" src="https://github.com/user-attachments/assets/4b597ea1-0787-4f18-aebc-f6d14cbcbf9e" />
