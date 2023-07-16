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
            <div class="picture"></div>
            <div style="display: flex; flex-direction: column; text-align: center; font-size: 40px;">
                <span style="font-weight: bold;">Lucas</span>
                <span>FAGET</span>
            </div>
            <div style="display: flex; flex-direction: column; text-align: center; font-size: 20px;">
                <span>Développeur web</span>
            </div>
            <div class="contact">
                <img style="width: 36px; height: 36px;" src="mail.svg" alt="mail" />
                <span>lucas.faget@laposte.net</span>
            </div>
            <div class="contact">
                <img style="width: 36px; height: 36px;" src="phone.svg" alt="phone" />
                <span>06.02.38.07.36</span>
            </div>
            <div class="flags">
                <img class="flag" src="france.svg" alt="france" />
                <img class="flag" src="united-kingdom.svg" alt="royaume-uni" />
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
        --aside-padding: 4mm;
    }

    main {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        gap: 20px;
        margin-block: 30px 50px;
        font-family: 'Roboto';
    }

    #cv {
        position: relative;
        width: 210mm;
        height: 297mm;
        display: flex;
        flex-direction: column;
    }

    .aside {
        background: var(--color-light);
        position: absolute;
        top: var(--padding);
        left: var(--padding);
        width: var(--aside-width);
        height: calc(var(--cv-height) - 2*var(--padding));
        border-radius: var(--aside-width);
        display: flex;
        flex-direction: column;
        gap: 8mm;
    }

    .picture {
        background: #fff;
        width: calc(var(--aside-width) - 2*var(--aside-padding));
        height: calc(var(--aside-width) - 2*var(--aside-padding));
        margin-block: var(--aside-padding) 0;
        margin-inline: var(--aside-padding);
        border-radius: 100%;
    }

    .contact {
        display: flex;
        flex-direction: column;
        align-items: center;
        gap: 2mm;
        text-align: center;
        font-size: 16px;
    }

    .flags {
        display: flex;
        justify-content: center;
        gap: 4mm;
    }

    .flag {
        width: 50px;
        height: 50px;
    }

    .header {
        background: var(--color-black);
        width: 100%;
        height: calc((var(--aside-width) / 2) + var(--padding));
    }

    .body {
        color: var(--color-white);
        background: var(--color-dark);
        width: 100%;
        flex: 1;
        padding-block: var(--padding);
        padding-inline: calc(2 * var(--padding) + var(--aside-width)) var(--padding);
    }
</style>
