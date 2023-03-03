
/**
 * Generates text using ChatGPT (gpt-3.5-turbo model).
 *
 * @param {string} secretKey - Secret Key.
 * @param {number} modelTemp - Temperature of the generated text between 0 - 2. 2 being the most creative.
 * @param {string} yourPrompt - Prompt to generate text from.
 * @return Response returned by gpt-3.5-turbo.
 * @customfunction
 */

function GPT(secretKey, modelTemp, yourPrompt) {
  // Define the URL for the gpt-3.5-turbo( API
  const url = "https://api.openai.com/v1/chat/completions";

  // Define the payload to be sent in the API request
  const payload = {
    model: "gpt-3.5-turbo",
    messages: [{"role": "user", "content": yourPrompt}],
    temperature: modelTemp
  };

  // Define the options for the API request
  const options = {
    contentType: "application/json",
    headers: { Authorization: "Bearer " + secretKey },
    payload: JSON.stringify(payload),
  };

  // Send the API request and parse the response as JSON
  const responseJson = JSON.parse(UrlFetchApp.fetch(url, options).getContentText());

  // Return the content from the assistant message in the response
  const assistantMessage = responseJson.choices.find(choice => choice.message.role === 'assistant');
  return assistantMessage ? assistantMessage.message.content.trim() : '';
}




/**
 * Generates images using DALLE model.
 *
 * @param {string} secretKey - Secret Key.
 * @param {number} size - Size of the generated image.
 * @param {string} yourPrompt - Prompt to generate an image from.
 * @return Response returned by DALLE.
 * @customfunction
 */


function DALLE(secretKey, size, yourPrompt) {
  // Define the URL for the DALLE API
  const url = 'https://api.openai.com/v1/images/generations';

  // Define the payload to be sent in the API request
  const payload = {
    prompt: yourPrompt,
    n: 1,
    size: size,
  };

  // Define the options for the API request
  const options = {
    method: 'post',
    contentType: 'application/json',
    headers: { Authorization: 'Bearer ' + secretKey },
    payload: JSON.stringify(payload),
  };

  // Send the API request and parse the response as JSON
  const responseJson = UrlFetchApp.fetch(url, options).getContentText();
  const imageUrl = JSON.parse(responseJson).data[0].url;

  // Log the generated image URL to the console
  Logger.log(imageUrl);

  // Return the generated image URL
  return imageUrl;
}
