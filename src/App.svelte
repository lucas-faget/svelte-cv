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
        
    </div>
</main>

<style>
    main {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        gap: 20px;
        margin-block: 50px;
    }

    #cv {
        background-color: red;
        width: 210mm;
        height: 297mm;
    }
</style>
