# just-a-bill-public
Serves as a description of the just-a-bill functionality
Try it [here](https://just-a-bill.netlify.app/)

What is the purpose of this site?
To provide users to insights on what their representatives are achieving in DC and utilize AI to explain bill texts in a comprehensive way

**How does it work?** <br>
  
  **Where does the data come from?** <br>
  The data is retrieved from the [congress.gov API](https://gpo.congress.gov/) using a Node server that I setup. This is an official API from the US government <br>
  
  **How does a user access the information?** <br>
  Originally, the user would ping the API anytime they wanted to pull data, this became taxing on the API rate limit of 5,000 requests per hour. Now they are accessing a local DB that is built into the code. <br>
  
  **How does the local DB update? Is the data fresh?** <br>
  The local DB updates using the existing API fetch code. I utlizied Github Actions to routinely run the fetch functions and write them into a local .json file. The states are broken into different files and run between every 12 and 24 hours. The users are notified         with the last time the data they are seeing is updated. The dataset is well under 5 MB and does not slow down the page load. <br>
  
  **5,000 requests per hour sounds like plenty to not need caching, why did you cache?** <br>
  There are a total of 535 members of the House and Senate combined. Each member sponsoring 100s, or in some case 1000s of bills a piece. Some of the data I am sending back to the user requires me to iterate through every congressmember for that state, and count            parameters from each bill they sponsored. So the requests can add up quickly. Also, waiting on the data from the API would take a while since I was iterating through so many bills and this presents data back to the user much faster.
  
  **Why did you go with this approach?** <br>
  I want to keep the infrastructure light so I can focus on data pipelines and new features for the user. Long term, I will integrate with a cloud DB. <br>

  **You said it uses AI, how does it do that?**
  Right now I am using OpenRouter to connect users to models that can quickly translate bill texts into readable and informative responses. Users can ask questions about the bill, and soforth. The user needs to load the bill into the AI so it has all the text directly in   the prompt and doesn't have to reach out to the internet to gather information.
    
    
    
