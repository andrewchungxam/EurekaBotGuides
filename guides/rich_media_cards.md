# Azure Bot Framework - Adding Rich Media Cards to Replies

### This guide will help you get going rich media cards so you can add some flare to your bot responses

When you've completed this tutorial, you should expect to see this:
<br/><img src="../screens/" /><br/><br/>

### What are [rich media cards](https://docs.microsoft.com/en-us/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp)?

Messages exchanged between user and bot can contain media attachments, such as images, video, audio, and files. The Bot Framework SDK supports the task of sending rich messages to the user. There are pre-built rich cards, such as VideoCard and HeroCard, but you can also define [your own UI using Adaptive Cards](https://adaptivecards.io/visualizer/).


### Section 1: Greet the user with a rich media card

1. Create a new folder in the root of your project called `Cards`

1. Add [this code](https://raw.githubusercontent.com/rob-derosa/EurekaBot/master/src/end_here/EurekaBot/Cards/WelcomeCard.cs) to a new file called `WelcomeCard.cs` to the `Cards` folder you created in the previous step

1. Inspect the minimal code in the `WelcomeCard.cs` file to understand how the rich card is created, specifically the use of config settings, media and buttons

1. We can greet the user by sending them a welcome message - in the `Bot.cs` file, add the following code into the `switch (turnContext.Activity.Type)` statement:
	```
	case ActivityTypes.ConversationUpdate:

		if (turnContext.Activity.MembersAdded != null)
		{
			var reply = turnContext.Activity.CreateReply();
			reply.Attachments.Add(new WelcomeCard(_configuration).ToAttachment());

			foreach (var newMember in turnContext.Activity.MembersAdded)
			{
				//Only send a notification to new members other than the bot
				if (newMember.Id != turnContext.Activity.Recipient.Id)
				{
					await turnContext.SendActivityAsync(reply);
				}
			}
		}

		break;
	```

	1. Still working on this section...