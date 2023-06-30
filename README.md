# Google Apps Script for Converting Google Documents to HTML and Saving to Google Drive: Iterating Through Document URLs in a Spreadsheet

This Google Apps Script is designed to convert a Google Document into an HTML file and save it on Google Drive. The script works by first iterating through a list of Google Document URLs stored in the first sheet of an active Google Spreadsheet. For each URL, it extracts the document ID and calls the ConvertGoogleDocToCleanHtml(id) function.

The ConvertGoogleDocToCleanHtml(id) function processes the content of each Google Document and converts it into clean HTML markup. This function handles various elements such as paragraphs, inline images, and list items, preserving their structure in the output HTML.

It calls other functions like processItem(child, listCounters, images), processText(item, output), and processImage(item, images, output) to process individual components of the Google Document, each serving a specific purpose:

**processItem(child, listCounters, images)**: This function handles different types of items found within the Google Document. It checks for the type of each item (paragraph, inline image, list item) and calls the appropriate function to handle that specific type. The converted HTML is then appended to an array which is returned as a string.

**processText(item, output)**: This function is responsible for processing and converting text elements into HTML, considering attributes such as bold, italic, underline, and handling hyperlinks.

**processImage(item, images, output)**: This function processes inline images in the Google Document, adding a reference to the image in the HTML output and storing the image blob to later be added to the same Google Drive folder.

After processing the Google Document content, ConvertGoogleDocToCleanHtml(id) calls saveHtmlToDrive(html, images, id).

The saveHtmlToDrive(html, images, id) function saves the generated HTML as a file in a specific Google Drive folder (indicated by folderId). It also saves all inline images encountered during the document processing stage into the same Google Drive folder.

It's important to note that, in the provided code, folderId is hard-coded, which means it will save the HTML and images into that specific Google Drive folder. You would need to replace it with your actual Google Drive folder ID to save files to your preferred location.

Finally, it seems there are a couple of unused functions in your script: createDocumentForHtml(html, images) and dumpAttributes(atts).
