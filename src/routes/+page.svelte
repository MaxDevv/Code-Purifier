<script>
	import { preventDefault } from "svelte/legacy";
	let title = "Purify";
    let extendedTitle = "The ultimate code cleaner!";
    // import CodeBox from "./CodeBox.svelte";
    let inputCode = $state("");
    let outputCode = $state("");
    function cleanCode(e) {
        if (!inputCode.trim()) return;
        outputCode = "Purifying... Please refresh page if stuck purifying";
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
<!-- <div class="background"><svg viewBox="0 0 1000 1000" xmlns="http://www.w3.org/2000/svg"><defs><radialGradient id="b" cx="50%" cy="50%" r="50%" fx="21%" fy="74%"><stop offset="0%" stop-color="#45f7ef"/><stop offset="100%" stop-color="rgba(69,122,247,0.2)"/></radialGradient><filter id="a" x="-500" y="-500" width="2000" height="2000" filterUnits="userSpaceOnUse"><feGaussianBlur in="SourceGraphic" stdDeviation="30"/></filter></defs><rect width="100%" height="100%" fill="transparent"/><g filter="url(#a)"><svg width="850" height="850" viewBox="0 0 500 500" xmlns="http://www.w3.org/2000/svg" transform="translate(31.301 85.385)"><path fill="url(#b)" d="M368 319.5q-38 69.5-125 82T110 332q-46-82 6-152.5t155.5-108Q375 34 390.5 142T368 319.5Z"/></svg></g><svg width="500" height="90.312" viewBox="0 0 1218 220" fill="none" xmlns="http://www.w3.org/2000/svg" transform="translate(250 454.844)"></svg></svg></div> -->
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
                <textarea autocomplete="off" autocorrect="off" autocapitalize="off" spellcheck="false" class="codeEditor" name="" id="" placeholder="Insert Code Here..." bind:value={inputCode} maxlength="5000"></textarea>
                <button type="submit">Purify</button>
                <textarea name="" id="" readonly>{outputCode}</textarea>
            </form>
    </div>
</div>

<style>
    div {
        display: flex;
    }
    :global(html) {
        flex-direction: column;
        background-color: #252525;
        overflow: scroll;
        overflow-x: hidden;
        /* background-image: url("data:image/svg+xml,%3Csvg%20viewBox%3D%220%200%201000%201000%22%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%3E%3Cdefs%3E%3CradialGradient%20id%3D%22b%22%20cx%3D%2250%25%22%20cy%3D%2250%25%22%20r%3D%2250%25%22%20fx%3D%2221%25%22%20fy%3D%2274%25%22%3E%3Cstop%20offset%3D%220%25%22%20stop-color%3D%22%2345f7ef%22%2F%3E%3Cstop%20offset%3D%22100%25%22%20stop-color%3D%22rgba(69%2C122%2C247%2C0.2)%22%2F%3E%3C%2FradialGradient%3E%3Cfilter%20id%3D%22a%22%20x%3D%22-500%22%20y%3D%22-500%22%20width%3D%222000%22%20height%3D%222000%22%20filterUnits%3D%22userSpaceOnUse%22%3E%3CfeGaussianBlur%20in%3D%22SourceGraphic%22%20stdDeviation%3D%2230%22%2F%3E%3C%2Ffilter%3E%3C%2Fdefs%3E%3Crect%20width%3D%22100%25%22%20height%3D%22100%25%22%20fill%3D%22transparent%22%2F%3E%3Cg%20filter%3D%22url(%23a)%22%3E%3Csvg%20width%3D%22850%22%20height%3D%22850%22%20viewBox%3D%220%200%20500%20500%22%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20transform%3D%22translate(31.301%2085.385)%22%3E%3Cpath%20fill%3D%22url(%23b)%22%20d%3D%22M368%20319.5q-38%2069.5-125%2082T110%20332q-46-82%206-152.5t155.5-108Q375%2034%20390.5%20142T368%20319.5Z%22%2F%3E%3C%2Fsvg%3E%3C%2Fg%3E%3Csvg%20width%3D%22500%22%20height%3D%2290.312%22%20viewBox%3D%220%200%201218%20220%22%20fill%3D%22none%22%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20transform%3D%22translate(250%20454.844)%22%3E%3C%2Fsvg%3E%3C%2Fsvg%3E");
        background-repeat: no-repeat;
        background-position: center center;
        -webkit-background-size: cover;
        -moz-background-size: cover;
        -o-background-size: cover;
        background-size: cover; */
        /* background-color: navy; */
        -ms-overflow-style: none;  /* Internet Explorer 10+ */
        scrollbar-width: none; /* Firefox */
    }::-webkit-scrollbar {
    display: none;
    width: 0;  /* Remove scrollbar space */
    background: transparent;  /* Optional: just make scrollbar invisible */
}

    .background {
        position: fixed;
        opacity: 80%;
        top: 50%;
        left: 50%;
        width: 200%;
        height: 200%;
        position: absolute;
        background: url("data:image/svg+xml,%3Csvg%20viewBox%3D%220%200%201000%201000%22%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%3E%3Cdefs%3E%3CradialGradient%20id%3D%22b%22%20cx%3D%2250%25%22%20cy%3D%2250%25%22%20r%3D%2250%25%22%20fx%3D%2221%25%22%20fy%3D%2274%25%22%3E%3Cstop%20offset%3D%220%25%22%20stop-color%3D%22%2345f7ef%22%2F%3E%3Cstop%20offset%3D%22100%25%22%20stop-color%3D%22rgba(69%2C122%2C247%2C0.2)%22%2F%3E%3C%2FradialGradient%3E%3Cfilter%20id%3D%22a%22%20x%3D%22-500%22%20y%3D%22-500%22%20width%3D%222000%22%20height%3D%222000%22%20filterUnits%3D%22userSpaceOnUse%22%3E%3CfeGaussianBlur%20in%3D%22SourceGraphic%22%20stdDeviation%3D%2230%22%2F%3E%3C%2Ffilter%3E%3C%2Fdefs%3E%3Crect%20width%3D%22100%25%22%20height%3D%22100%25%22%20fill%3D%22transparent%22%2F%3E%3Cg%20filter%3D%22url(%23a)%22%3E%3Csvg%20width%3D%22850%22%20height%3D%22850%22%20viewBox%3D%220%200%20500%20500%22%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20transform%3D%22translate(31.301%2085.385)%22%3E%3Cpath%20fill%3D%22url(%23b)%22%20d%3D%22M368%20319.5q-38%2069.5-125%2082T110%20332q-46-82%206-152.5t155.5-108Q375%2034%20390.5%20142T368%20319.5Z%22%2F%3E%3C%2Fsvg%3E%3C%2Fg%3E%3Csvg%20width%3D%22500%22%20height%3D%2290.312%22%20viewBox%3D%220%200%201218%20220%22%20fill%3D%22none%22%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20transform%3D%22translate(250%20454.844)%22%3E%3C%2Fsvg%3E%3C%2Fsvg%3E") no-repeat center center;
        animation: rotateBackground 60s linear infinite;
        z-index: -1;
        /* background-repeat: no-repeat;
        background-position: center center;
        -webkit-background-size: cover;
        -moz-background-size: cover;
        -o-background-size: cover;
        background-size: cover; */
        -ms-overflow-style: none;  /* Internet Explorer 10+ */
        scrollbar-width: none; /* Firefox */
    }::-webkit-scrollbar {
    display: none;
    width: 0;  /* Remove scrollbar space */
    background: transparent;  /* Optional: just make scrollbar invisible */
}


    @keyframes rotateBackground {
        from {
            transform: translate(-50%, -50%) rotate(0deg);
        }
        to {
            transform: translate(-50%, -50%) rotate(360deg);
        }
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
