# just-a-bill-public
Serves as a description of the just-a-bill functionality
Try it [here](https://just-a-bill.netlify.app/)

What is the purpose of this site?
To provide users to insights on what their representatives are achieving in DC and utilize AI to explain bill texts in a comprehensive way

How does it work?
    Where does the data come from?
    The data is retrieved from the [congress.gov API](https://gpo.congress.gov/). This is an official API from the US government
    How does a user access the information?
    Originally, the user would ping the API anytime they wanted to pull data, this became taxing on the API rate limit of 5,000 requests per hour. Now they are accessing a local DB that is built into the code.
    How does the local DB update? Is the data fresh?
    The local DB updates using the existing API fetch code. I utlizied Github Actions to routinely run the fetch functions and write them into a local .json file. The states are broken into different files and run between every 12 and 24 hours. The users are notified         with the last time the data they are seeing is updated. The dataset is well under 5 MB and does not slow down the page load.
    5,000 requests per hour sounds like plenty to not need caching, why did you cache?
    There are a total of 535 members of the House and Senate combined. Each member sponsoring 100s, or in some case 1000s of bills a piece. Some of the data I am sending back to the user requires me to iterate through every congressmember for that state, and count 
    
