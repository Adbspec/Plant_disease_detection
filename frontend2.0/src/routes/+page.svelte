<script>
    import { onMount } from "svelte";

    let response = {};
    let selectedImagePreview = null;
    let success = false;

    async function uploadFile() {
        const fileInput = document.getElementById("fileInput");
        const file = fileInput.files[0];
        if (!file) {
            alert("Please select a file.");
            return;
        }

        console.log(file);
        const formData = new FormData();
        formData.append("file", file);

        try {
            const res = await fetch("http://localhost:8000/predict", {
                // Change this URL to your server endpoint
                method: "POST",
                body: formData,
            });
            response = await res.json();
            success = true;
            showResponse();
        } catch (error) {
            console.error("Error:", error);
            response = { error: "Failed to process the file." };
        }
    }

    function showResponse() {
        const responseOutput = document.getElementById("responseOutput");
        if (response.class && response.confidence) {
            responseOutput.innerText = `
                Class: ${response.class}
                Confidence: ${(Number(response.confidence) * 100).toFixed(2)}%
                `;
        } else {
            responseOutput.innerText = "";
        }
    }

    function onImageSelected(event) {
        const file = event.target.files[0];
        if (!file) return;

        const reader = new FileReader();
        reader.onloadend = () => {
            selectedImagePreview = reader.result;
        };
        reader.readAsDataURL(file);
    }

    function reload() {
        window.location.href = window.location.href;
    }
    onMount(() => {
        showResponse();
    });
</script>

<h4 class="header">Plant Disease Detection</h4>
<div class="container-main">
    <div class="row">
        <div class="card" style="position: relative;top:5rem">
            <!-- Hidden file input -->
            <input
                type="file"
                id="fileInput"
                style="display: none;"
                on:change={onImageSelected}
            />

            <!-- Clickable icon as a box (without the SVG icon) -->
            <label class="upload-icon" for="fileInput">
                {#if selectedImagePreview}
                    <img
                        src={selectedImagePreview}
                        alt="Selected Image Preview"
                        style="max-width: 100%; max-height: 100%;"
                    />
                {/if}
            </label>
            <br />
            <button on:click={uploadFile}>Upload</button>
            <button on:click={reload} style="background-color: #4f7bf5;"
                >Reset</button
            >
        </div>
        <br />
        <div style="position: relative;top:3rem;text-align:left" class={success ? "card" : "hide"}>
            <h2>Response:</h2>
            <h3 id="responseOutput" />
        </div>
    </div>
</div>

<style>
    .hide {
        display: none;
    }
    .upload-icon {
        display: inline-block;
        width: 15rem;
        height: 15rem;
        border: 2px solid gray;
        border-radius: 4px;
        cursor: pointer;
        text-align: center;
        line-height: 5rem;
    }
    .row {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }
    button {
        background-color: #7c6abe;
        border: none;
        color: white;
        padding: 15px 32px;
        text-align: center;
        text-decoration: none;
        font-size: 16px;
        border-radius: 12px;
        margin: 4px 2px;
        cursor: pointer;
    }
    .container-main {
        height: 100vh;
        width: 100%;
        background: url("./bg.jpg");
        backdrop-filter: blur(5px);
        background-size: cover;
        background-repeat: no-repeat;
    }

    .header {
        display: flex;
        align-items: center;
        min-height: 56px;
        background: #062705;
        color: #fff;
        padding-left: 16px;
        padding-right: 16px;
    }

    .card {
        background-color: rgba(255, 255, 255, 0.7);
        border-radius: 50px;
        border-radius: 10px;
        padding: 20px;
        margin: 20px;
        text-align: center;
        max-width: 400px;
        box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    }
</style>
