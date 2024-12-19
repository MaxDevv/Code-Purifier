<script>
	import { preventDefault } from "svelte/legacy";
	let title = "Purify";
    let extendedTitle = "The ultimate code cleaner!";
    // import CodeBox from "./CodeBox.svelte";
    let inputCode = $state("");
    let outputCode = $state("");
    function cleanCode(e) {
        if (!inputCode.trim()) return;
        outputCode = "Purifying...";
        puter.ai.chat(`You are being used in an API please only respond with the data requested. You are to remmove all sensitive information (including but not limited to: API Keys, Access Tokens, Usernames and Passwords, SSH Keys, Database Credentials, Full Names, Email Addresses, Phone Numbers, Home Addresses, Social Security Numbers (SSNs), National ID Numbers, Credit Card Numbers, Bank Account Details, Cryptocurrency Wallet Keys, Encryption Keys, Certificate Files (.pem, .crt, .key), VPN Configurations, Firewall Rules and Configs, Source Code, Internal Documentation, Internal Emails or Communication Logs, Server IPs and Ports, Environment Variables (.env files), Debug Logs, Backup Files and Database Dumps, Contracts.) From this code, replace the sensitive information with the string "REDACTED_SENSITIVE_INFORMATION". Here is the code: "${inputCode}"`).then((response) => {
            console.log(response);
            outputCode = response.message.content;
        });
    }
// function createCodeEditor(textareaElement, options = {}) {
//     // Default options
//     const defaultOptions = {
//         mode: 'javascript',          // Default language mode
//         theme: 'dracula',           // Editor theme
//         lineNumbers: true,          // Show line numbers
//         autoCloseBrackets: true,    // Automatically close brackets
//         matchBrackets: true,        // Highlight matching brackets
//         indentUnit: 4,             // Indent size
//         tabSize: 4,                // Tab size
//         lineWrapping: true,        // Wrap long lines
//         height: '300px'            // Editor height
//     };

//     // Merge default options with user provided options
//     const editorOptions = { ...defaultOptions, ...options };

//     // Create the CodeMirror editor
//     const editor = CodeMirror.fromTextArea(textareaElement, editorOptions);
    
//     // Set the height
//     editor.setSize(null, editorOptions.height);
    
//     return editor;
// }

</script>

<svelte:head>
	<title>{title} | {extendedTitle}</title>
    <script src="https://js.puter.com/v2/"></script>
    <!-- <link href="https://cdnjs.cloudflare.com/ajax/libs/codemirror/5.65.2/codemirror.min.css" rel="stylesheet">
    <link href="https://cdnjs.cloudflare.com/ajax/libs/codemirror/5.65.2/theme/dracula.min.css" rel="stylesheet">
    <script src="https://cdnjs.cloudflare.com/ajax/libs/codemirror/5.65.2/codemirror.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/codemirror/5.65.2/mode/javascript/javascript.min.js"></script> -->
</svelte:head>
<div class="background"></div>
<div class="body">
   <div class="navbar">
        <h2>{title} :D</h2>
        <div class="navbar-border"></div>
    </div>
    <div class="mainContainer">    
        <!-- <h1 style="font-weight: bold;">Purify</h1> -->
        <div class="subTitle">
            <h1>{title}</h1>
            <h1>|</h1>
            <h3>{extendedTitle}</h3>
        </div>
        <h5>Removes all sensitive information from your code.</h5>
            <form   onsubmit={(e) => {preventDefault();cleanCode(e);}}>
                <!-- <CodeBox type="input" /> -->
                <textarea class="codeEditor" name="" id="" placeholder="Insert Code Here..." bind:value={inputCode} maxlength="5000"></textarea>
                <button type="submit">Purify</button>
                <textarea name="" id="" readonly>{outputCode}</textarea>
            </form>
    </div>
</div>

<style>
    div {
        display: flex;
    }
    :global(body) {
        flex-direction: column;
        background-color: #252525;
        /* background-color: navy; */
    }
	* {
		font-family:
			ui-sans-serif,
			system-ui,
			sans-serif,
			Apple Color Emoji,
			Segoe UI Emoji,
			Segoe UI Symbol,
			Noto Color Emoji;
        font-weight: normal;
        /* border:1px solid red; */
        color: #dbf1f3;
	}

    .navbar-border {
        border-bottom: 1px solid wheat;   
        width: 99%;
        position: absolute;
        align-self: flex-end;
        
    }
    .mainContainer {
        flex-direction: column;
        align-items: center;
    }

    .subTitle {
        flex-direction: row;
        align-items: center;
        gap: 0.5em;
        opacity: 80%;
    }
    .navbar {
        align-self: baseline;
        font-weight: bolder;
        opacity: 70%;
    }
    .body {
        flex-direction: column;
        gap: 2em;
        align-items: center;
    }

    button {
        align-self: flex-end;
        margin-right: 1rem;
        font-size: large;
        font-weight: 450;
        padding-left: 1.25em;
        padding-right: 1.25em;
        padding-top: 0.25em;
        padding-bottom: 0.25em;
        color: white;
        background-color: rgba(82, 135, 151, 0.75);
        border-radius: 0.35em;
        border: none;
        cursor: pointer;
    }

    /* .subContainer {
        display: flex;
        border: 1px solid white;
        padding: 1.5em;
        border-radius: 1em;
        background-color: rgba(0, 0, 0, 0.2);
        align-items: center;
        
    } */

    form {
        display: flex;
        border: 1px solid white;
        padding: 1em;
        padding-left: 0.5em;
        padding-right: 0.5em;
        border-radius: 1em;
        background-color: rgba(0, 0, 0, 0.2);
        align-items: center;
        flex-direction: column;
        gap: 1em;
        width: 100%;
    }

    textarea {
        width: 60em;   
        background-color: rgba(0, 0, 0, 0);
        border: 1px solid white;
        border-radius: 0.5em;
        padding: 0.5em;
        height: 20em;
    }

    h5 {
        opacity: 40%;
    }

</style>
