---
lab:
    title: 'Analyze Video with Video Analyzer'
    module: 'Module 8 - Getting Started with Azure AI Vision'
---

# Analyze Video with Video Analyzer

A large proportion of the data created and consumed today is in the format of video. **Azure AI Video Indexer** is an AI-powered service that you can use to index videos and extract insights from them.

> **Note**: From June 21st 2022, capabilities of Azure AI services that return personally identifiable information are restricted to customers who have been granted [limited access](https://docs.microsoft.com/azure/cognitive-services/cognitive-services-limited-access). Without getting limited access approval, recognizing people and celebrities with Video Analyzer for this lab is not available. For more details about the changes Microsoft has made, and why - see [Responsible AI investments and safeguards for facial recognition](https://azure.microsoft.com/blog/responsible-ai-investments-and-safeguards-for-facial-recognition/).

## Clone the repository for this course

If you have recently cloned **mslearn-ai-vision** code repository to the environment where you're working on this lab, open it in Visual Studio Code; otherwise, follow these steps to clone it now.

1. Start Visual Studio Code.
2. Open the palette (SHIFT+CTRL+P) and run a **Git: Clone** command to clone the `https://github.com/MicrosoftLearning/mslearn-ai-vision` repository to a local folder (it doesn't matter which folder).
3. When the repository has been cloned, open the folder in Visual Studio Code.
4. Wait while additional files are installed to support the C# code projects in the repo.

    > **Note**: If you are prompted to add required assets to build and debug, select **Not Now**.

## Upload a video to Video Analyzer

First, you'll need to sign into the Video Analyzer portal and upload a video.

> **Tip**: If the Video Analyzer page is slow to load in the hosted lab environment, use your locally installed browser. You can switch back to the hosted VM for the later tasks.

1. In your browser, open the Video Analyzer portal at `https://www.videoindexer.ai`.
2. If you have an existing Video Analyzer account, sign in. Otherwise, sign up for a free account and sign in using your Microsoft account (or any other valid account type). If you have difficulty signing in, try opening a private browser session.
3. In Video Analyzer, select the **Upload** option. Then select the option to **Enter URL**, enter `https://aka.ms/responsible-ai-video` and click **Add**. Change the default name to **Responsible AI**, review the default settings, select the checkbox to verify compliance with Microsoft's policies for facial recognition, and upload the file.
4. After the file has uploaded, wait a few minutes while Video Analyzer automatically indexes it.

> **Note**: In this exercise, we're using this video to explore Video Analyzer functionality; but you should take the time to watch it in full when you've finished the exercise as it contains useful information and guidance for developing AI-enabled applications responsibly! 

## Review video insights

The indexing process extracts insights from the video, which you can view in the portal.

1. In the Video Analyzer portal, when the video is indexed, select it to view it. You'll see the video player alongside a pane that shows insights extracted from the video.

    > **Note**: Due to the limited access policy to protect individuals identities, you may not see names when you index the video.

![Video Analyzer with a video player and Insights pane](../media/video-indexer-insights.png)

2. As the video plays, select the **Timeline** tab to view a transcript of the video audio.

![Video Analyzer with a video player and Timeline pane showing the video transcript.](../media/video-indexer-transcript.png)

3. At the top right of the portal, select the **View** symbol (which looks similar to &#128455;), and in the list of insights, in addition to **Transcript**, select **OCR** and **Speakers**.

![Video Analyzer view menu with Transcript, OCR, and Speakers selected](../media/video-indexer-view-menu.png)

4. Observe that the **Timeline** pane now includes:
    - Transcript of audio narration.
    - Text visible in the video.
    - Indications of speakers who appear in the video. Some well-known people are  automatically recognized by name, others are indicated by number (for example *Speaker #1*).
5. Switch back to the **Insights** pane and view the insights show there. They include:
    - Individual people who appear in the video.
    - Topics discussed in the video.
    - Labels for objects that appear in the video.
    - Named entities, such as people and brands that appear in the video.
    - Key scenes.
6. With the **Insights** pane visible, select the **View** symbol again, and in the list of insights, add **Keywords** and **Sentiments** to the pane.

    The insights found can help you determine the main themes in the video. For example, the **topics** for this video show that it is clearly about technology, social responsibility, and ethics.

## Search for insights

You can use Video Analyzer to search the video for insights.

1. In the **Insights** pane, in the **Search** box, enter *Bee*. You may need to scroll down in the Insights pane to see results for all types of insight.
2. Observe that one matching *label* is found, with its location in the video indicated beneath.
3. Select the beginning of the section where the presence of a bee is indicated, and view the video at that point (you may need to pause the video and select carefully - the bee only appears briefly!)
4. Clear the **Search** box to show all insights for the video.

![Video Analyzer search results for Bee](../media/video-indexer-search.png)

## Use Video Analyzer widgets

The Video Analyzer portal is a useful interface to manage video indexing projects. However, there may be occasions when you want to make the video and its insights available to people who don't have access to your Video Analyzer account. Video Analyzer provides widgets that you can embed in a web page for this purpose.

1. In Visual Studio Code, in the **06-video-indexer** folder, open **analyze-video.html**. This is a basic HTML page to which you will add the Video Analyzer **Player** and **Insights** widgets. Note the reference to the **vb.widgets.mediator.js** script in the header - this script enables multiple Video Analyzer widgets on the page to interact with one another.
2. In the Video Analyzer portal, return to the **Media files** page and open your **Responsible AI** video.
3. Under the video player, select **&lt;/&gt; Embed** to view the HTML iframe code to embed the widgets.
4. In the **Share and Embed** dialog box, select the **Player** widget, set the video size to 560 x 315, and then copy the embed code to the clipboard.
5. In Visual Studio Code, in the **analyze-video.html** file, paste the copied code under the comment **&lt;-- Player widget goes here -- &gt;**.
6. Back in the **Share and Embed** dialog box, select the **Insights** widget and then copy the embed code to the clipboard. Then close the **Share and Embed** dialog box, switch back to Visual Studio Code, and paste the copied code under the comment **&lt;-- Insights widget goes here -- &gt;**.
7. Save the file. Then in the **Explorer** pane, right-click **analyze-video.html** and select **Reveal in File Explorer**.
8. In File Explorer, open **analyze-video.html** in your browser to see the web page.
9. Experiment with the widgets, using the **Insights** widget to search for insights and jump to them in the video.

![Video Analyzer widgets in a web page](../media/video-indexer-widgets.png)
