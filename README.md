This single page was inspired by @varunshenoy's https://github.com/varunshenoy/GraphGPT

## How to use

Ask a GPT model like https://github.com/varunshenoy/GraphGPT/blob/main/public/prompts/main.prompt

For instance:

We could ask ChatGPT this:

```
Given the current state of a graph and a prompt, extrapolate as many relationships as possible from the prompt and update the state. Every node has an id, label, and color (in hex). Every edge has a to and from with node ids, and a label. Edges are directed, so the order of the from and to is important.

Examples:
current state:
{ "counter": 1, "graph": { "nodes": [], "edges": [] } }

prompt: Alice is Bob's roommate. Make new nodes in random different colors.

new state:
{ "counter": 2, "graph": { "nodes": [ { "id": 1, "label": "Bob", "color": "#ffffff" }, { "id": 2, "label": "Alice", "color": "#ff7675" } ], "edges": [ { "from": 1, "to": 2, "label": "roommate" }, ] } }

current state:
{ "counter": 1, "graph": { "nodes": [], "edges": [] } }

prompt: 在《西游记》中，唐僧是主要人物，他的三徒弟猪八戒、沙僧和孙悟空在整个故事中给唐僧带来了很多帮助和麻烦。孙悟空是三徒弟中最强大的一位，他因为自身的强大和机智，使得唐僧能够顺利地完成取经任务。然而，孙悟空也是最顽皮和好动的一位，他经常在路途中惹事生非，给唐僧和其他人带来麻烦。白骨精是故事中的反派人物，她的出现给唐僧和三徒弟带来了很多阻碍和困难。如来佛祖则是一位至高无上的神祇，他的出现给故事增添了很多神秘感和宗教色彩。总的来说，这些人物在故事中互相影响、相互依存，通过他们的相互作用和互动，使得故事充满了生气和悬念，对读者产生了很大的吸引力。让 node 颜色随机分配。

new state:

```

Then the answer could be as the follow. We could paste it into the render and it will be renderred like:

<img width="621" src="https://user-images.githubusercontent.com/1651790/217431711-9c4f8803-5254-463e-8248-a78913341c4e.png">


> The result:
> - Note, I know the color part is silly for now, PR is welcomed!

```json
{
   "counter":7,
   "graph":{
      "nodes":[
         {
            "id":1,
            "label":"唐僧",
            "color":"#ff7675"
         },
         {
            "id":2,
            "label":"猪八戒",
            "color":"#ffffff"
         },
         {
            "id":3,
            "label":"沙僧",
            "color":"#aaa"
         },
         {
            "id":4,
            "label":"孙悟空",
            "color":"#ddd"
         },
         {
            "id":5,
            "label":"白骨精",
            "color":"#ccc"
         },
         {
            "id":6,
            "label":"如来佛祖",
            "color":"#bbb"
         }
      ],
      "edges":[
         {
            "from":1,
            "to":2,
            "label":"三徒弟"
         },
         {
            "from":1,
            "to":3,
            "label":"三徒弟"
         },
         {
            "from":1,
            "to":4,
            "label":"三徒弟"
         },
         {
            "from":4,
            "to":1,
            "label":"帮助"
         },
         {
            "from":4,
            "to":1,
            "label":"麻烦"
         },
         {
            "from":5,
            "to":1,
            "label":"阻碍"
         },
         {
            "from":5,
            "to":2,
            "label":"阻碍"
         },
         {
            "from":5,
            "to":3,
            "label":"阻碍"
         },
         {
            "from":5,
            "to":4,
            "label":"阻碍"
         },
         {
            "from":6,
            "to":1,
            "label":"增添神秘感"
         },
         {
            "from":6,
            "to":2,
            "label":"增添神秘感"
         },
         {
            "from":6,
            "to":3,
            "label":"增添神秘感"
         },
         {
            "from":6,
            "to":4,
            "label":"增添神秘感"
         },
         {
            "from":6,
            "to":5,
            "label":"增添神秘感"
         }
      ]
   }
}
```
