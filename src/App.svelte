<script lang="ts">
    import './app.css';

    import html2pdf from 'html2pdf.js';

    function generatePDF() {
        const content: HTMLElement = document.querySelector('#cv') as HTMLElement;
        const opt = {
            margin:       0,
            filename:     'CV_FAGET_Lucas.pdf',
            image:        { type: 'jpeg', quality: 0.98 },
            html2canvas:  { scale: 2 },
            jsPDF:        { unit: 'mm', format: 'a4', orientation: 'portrait' }
        };
  
        html2pdf().set(opt).from(content).save();
    }
</script>

<main>
    <button on:click={generatePDF}>Télécharger en PDF</button>

    <div id="cv">
        <div class="aside">
            <div class="picture">

            </div>
        </div>

        <div class="header">

        </div>
        <div class="body">
            Hello
        </div>
    </div>
</main>

<style>
    :root {
        --cv-width: 210mm;
        --cv-height: 297mm;

        --padding: 8mm;
 
        --aside-width: 63mm;
        --picture-size: 55mm;
    }

    main {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        gap: 20px;
        margin-block: 30px 50px;
    }

    #cv {
        position: relative;
        width: 210mm;
        height: 297mm;
        display: flex;
        flex-direction: column;
    }

    .aside {
        background: red;
        position: absolute;
        top: var(--padding);
        left: var(--padding);
        width: var(--aside-width);
        height: calc(var(--cv-height) - 2*var(--padding));
        border-radius: var(--aside-width);
    }

    .picture {
        position: absolute;
        top: calc((var(--aside-width) - var(--picture-size)) / 2);
        left: calc((var(--aside-width) - var(--picture-size)) / 2);
        background: #fff;
        width: var(--picture-size);
        height: var(--picture-size);
        border-radius: 100%;
    }

    .header {
        background: #000;
        width: 100%;
        height: calc((var(--aside-width) / 2) + var(--padding));
    }

    .body {
        background: blue;
        width: 100%;
        flex: 1;
        padding-block: var(--padding);
        padding-inline: calc(2 * var(--padding) + var(--aside-width)) var(--padding);
    }
</style>
