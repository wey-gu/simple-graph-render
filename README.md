This single page was inspired by @varunshenoy's https://github.com/varunshenoy/GraphGPT

## How to use

Ask a GPT model like https://github.com/varunshenoy/GraphGPT/blob/main/public/prompts/main.prompt

For instance:

We could ask ChatGPT this:

```
Given the current state of a graph and a prompt,
extrapolate as many relationships as possible from the prompt and update the state.
Every node has an id, label, and color (in hex), the color of a node is randomly chosen from (6096B4, 93BFCF, BDCDD6, EEE9DA, F0EEED, 609EA2, C92C6D).
Every edge has a to and from with node ids, and a label.
Edges are directed, so the order of the from and to is important.

Examples:
current state:
{ "counter": 1, "graph": { "nodes": [], "edges": [] } }

prompt: Alice is Bob's roommate. Bob lives in the same apartment as Alice in New York.

new state:
{ "counter": 2, "graph": { "nodes": [ { "id": 1, "label": "Alice", "color": "#6096B4" }, { "id": 2, "label": "Bob", "color": "#6096B4" }, { "id": 3, "label": "New York", "color": "#93BFCF"} ], "edges": [ { "from": 1, "to": 2, "label": "roommate" }, { "from": 2, "to": 1, "label": "roommate" }, { "from": 2, "to": 1, "label": "lives in the same apartment as" } ] } }

current state:
{ "counter": 0, "graph": { "nodes": [], "edges": [] } }

prompt: 在英国作家J. K. 罗琳所著的一系列小说哈利波特中，主角哈利波特是一个典型的青少年角色，生活在魔法世界里。他是一位有着极高勇气和忠诚的魔法师，在魔法世界中有着极高的声望。他在霍格沃茨魔法学校学习魔法，并在那里结识了罗恩、赫敏、金妮、多比、纳威等朋友。哈利波特系列是一部关于哈利波特的魔法世界的故事。
霍格沃茨是一个位于英国的魔法学校，是世界上最著名的魔法学校之一。学校内有许多神奇的建筑，如大礼堂、庭院、图书馆等，以及各种奇妙的生物，如麻瓜、精灵、巨型犬等。在霍格沃茨，哈利学习了各种魔法技巧，包括咒语、催眠术、变形术等。
霍格沃茨的死亡场是哈利波特系列的一个关键事件，是哈利与黑魔法师伏地魔的最后一战。死亡场是一个巨大的战斗，哈利和他的朋友与黑魔法师和他的手下展开了一场激烈的战斗。在这场战斗中，哈利证明了自己是一个有着极高勇气和忠诚的魔法师，并最终战胜了黑魔法师。

new state:

```

Then the answer could be as the follow. We could paste it into the render and it will be renderred like:

<img width="623" src="https://user-images.githubusercontent.com/1651790/217442436-e09810cc-b016-4a85-9fa7-c970094f7907.png">


> The result:

```json
{
   "counter":8,
   "graph":{
      "nodes":[
         {
            "id":1,
            "label":"J.K. Rowling",
            "color":"#6096B4"
         },
         {
            "id":2,
            "label":"哈利波特",
            "color":"#93BFCF"
         },
         {
            "id":3,
            "label":"魔法世界",
            "color":"#BDCDD6"
         },
         {
            "id":4,
            "label":"霍格沃茨",
            "color":"#EEE9DA"
         },
         {
            "id":5,
            "label":"英国",
            "color":"#F0EEED"
         },
         {
            "id":6,
            "label":"霍格沃茨魔法学校",
            "color":"#609EA2"
         },
         {
            "id":7,
            "label":"罗恩",
            "color":"#C92C6D"
         },
         {
            "id":8,
            "label":"赫敏",
            "color":"#EEE9DA"
         },
         {
            "id":9,
            "label":"金妮",
            "color":"#6096B4"
         },
         {
            "id":10,
            "label":"多比",
            "color":"#93BFCF"
         },
         {
            "id":11,
            "label":"纳威",
            "color":"#BDCDD6"
         },
         {
            "id":12,
            "label":"死亡场",
            "color":"#EEE9DA"
         },
         {
            "id":13,
            "label":"黑魔法师",
            "color":"#F0EEED"
         }
      ],
      "edges":[
         {
            "from":1,
            "to":2,
            "label":"作者"
         },
         {
            "from":2,
            "to":3,
            "label":"生活在"
         },
         {
            "from":2,
            "to":4,
            "label":"学习魔法在"
         },
         {
            "from":4,
            "to":5,
            "label":"位于"
         },
         {
            "from":4,
            "to":6,
            "label":"是"
         },
         {
            "from":2,
            "to":7,
            "label":"结识"
         },
         {
            "from":2,
            "to":8,
            "label":"结识"
         },
         {
            "from":2,
            "to":9,
            "label":"结识"
         },
         {
            "from":2,
            "to":10,
            "label":"结识"
         },
         {
            "from":2,
            "to":11,
            "label":"结识"
         },
         {
            "from":2,
            "to":12,
            "label":"参加战斗"
         },
         {
            "from":2,
            "to":13,
            "label":"与战斗"
         },
         {
            "from":12,
            "to":2,
            "label":"是哈利波特与黑魔法师伏地魔的最后一战"
         }
      ]
   }
}
```
