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
            <div class="flex flex-column text-center" style="font-size: 40px;">
                <span class="text-bold">Lucas</span>
                <span>FAGET</span>
            </div>
            <div class="flex flex-column text-center" style="font-size: 20px;">
                <span class="text-bold">Développeur web</span>
            </div>
            <div class="flex flex-column" style="gap: 4mm;">
                <div class="contact">
                    <img class="contact-icon" src="icons/github.svg" alt="github" />
                    <span>https://github.com/lucas-faget</span>
                </div>
                <div class="contact">
                    <img class="contact-icon" src="icons/mail.svg" alt="mail" />
                    <span>lucas.faget@laposte.net</span>
                </div>
                <div class="contact">
                    <img class="contact-icon" src="icons/phone.svg" alt="phone" />
                    <span>06.02.38.07.36</span>
                </div>
            </div>
            <div class="flags">
                <img class="flag" src="flags/france.svg" alt="france" />
                <img class="flag" src="flags/united-kingdom.svg" alt="royaume-uni" />
            </div>
            <div class="flex flex-column" style="gap: 4mm;">
                <span class="text-center text-uppercase" style="font-size: 25px;">Intérêts</span>
                <div class="interests" style="gap: 2mm;">
                    <img class="interest-icon" src="icons/coding.svg" alt="coding" />
                    <img class="interest-icon" src="icons/gaming.svg" alt="coding" />
                    <img class="interest-icon" src="icons/cycling.svg" alt="coding" />
                </div>
            </div>
        </div>

        <div class="header"></div>
        <div class="body">
            <div class="flex flex-column">
                <span class="title">Expérience</span>
                <div class="separator-line"></div>
            </div>
            <div class="timeline">
                <div class="event">
                    <div class="date">
                        <span>2022 - 2023</span>
                    </div>
                    <div class="line">
                        <div class="point"></div>
                    </div>
                    <div class="flex flex-column" style="gap: 2mm; padding-bottom: 8mm;">
                        <span class="color-gold">Alternant développeur web (13 mois)</span>
                        <span class="color-gray" style="font-size: 14px;">Simpliciti - Lormont (33310)</span>
                        <ul style="font-size: 14px;">
                            <li>Développemnt de fonctionnalités et maintenance de EcoboxCarto: Application web d'optimisation de circuits de collecte</li>
                            <li>SIG / PHP / JS / MySQL / Postgres</li>
                            <li>Gestion de projet (SCRUM, Git, EasyRedmine)</li>
                        </ul>
                    </div>
                </div>
                <div class="event">
                    <div class="date">
                        <span>2021</span>
                    </div>
                    <div class="line">
                        <div class="point"></div>
                    </div>
                    <div class="flex flex-column" style="gap: 2mm;">
                        <span class="color-gold">Stage en développement web (2 mois)</span>
                        <span class="color-gray" style="font-size: 14px;">Audit Action plus - Toulouse</span>
                        <ul style="font-size: 14px;">
                            <li>Développement d'un ERP</li>
                            <li>PHP / JS / MySQL</li>
                        </ul>
                    </div>
                </div>
            </div>

            <div class="flex flex-column">
                <span class="title">Formation</span>
                <div class="separator-line"></div>
            </div>
            <div class="timeline">
                <div class="event">
                    <div class="date">
                        <span>2022 - 2023</span>
                    </div>
                    <div class="line">
                        <div class="point"></div>
                    </div>
                    <div class="description" style="padding-bottom: 8mm;">
                        <span class="color-gold">Licence Professionelle DAWIN</span>
                        <span class="color-gray" style="font-size: 14px;">IUT de Bordeaux</span>
                        <span style="font-size: 14px;">Développement en applications web et innovation numérique en alternance</span>
                    </div>
                </div>
                <div class="event">
                    <div class="date">
                        <span>2020 - 2022</span>
                    </div>
                    <div class="line">
                        <div class="point"></div>
                    </div>
                    <div class="description">
                        <span class="color-gray" style="font-size: 14px;">IUT de Toulouse</span>
                        <span class="color-gold">DUT Informatique</span>
                    </div>
                </div>
            </div>

            <div class="flex flex-column">
                <span class="title">Technos</span>
                <div class="separator-line"></div>
            </div>
            <!-- Stack -->
            <div class="flex flex-column" style="gap: 8mm;">
                <div class="flex align-center" style="gap: 8mm;">
                    <div class="flex" style="gap: 2mm;">
                        <img class="star" src="icons/gold-star.svg" alt="star" />
                        <img class="star" src="icons/gold-star.svg" alt="star" />
                        <img class="star" src="icons/gold-star.svg" alt="star" />
                    </div>
                    <div class="flex" style="gap: 4mm;">
                        <img class="techno" src="stack/typescript.svg" alt="typescript" />
                        <img class="techno" src="stack/javascript.svg" alt="javascript" />
                        <img class="techno" src="stack/php.svg" alt="php" />
                        <img class="techno" src="stack/database.svg" alt="database" />
                        <img class="techno" src="stack/git.svg" alt="git" />
                    </div>
                </div>
                <div class="flex align-center" style="gap: 8mm;">
                    <div class="flex" style="gap: 2mm;">
                        <img class="star" src="icons/gold-star.svg" alt="star" />
                        <img class="star" src="icons/gold-star.svg" alt="star" />
                        <img class="star" src="icons/black-star.svg" alt="star" />
                    </div>
                    <div class="flex" style="gap: 4mm;">
                        <img class="techno" src="stack/vue.svg" alt="vue" />
                        <img class="techno" src="stack/svelte.svg" alt="svelte" />
                        <img class="techno" src="stack/laravel.svg" alt="laravel" />
                        <img class="techno" src="stack/linux.svg" alt="linux" />
                    </div>
                </div>
                <div class="flex align-center" style="gap: 8mm;">
                    <div class="flex" style="gap: 2mm;">
                        <img class="star" src="icons/gold-star.svg" alt="star" />
                        <img class="star" src="icons/black-star.svg" alt="star" />
                        <img class="star" src="icons/black-star.svg" alt="star" />
                    </div>
                    <div class="flex" style="gap: 4mm;">
                        <img class="techno" src="stack/react.svg" alt="react" />
                        <img class="techno" src="stack/symfony.svg" alt="symfony" />
                        <img class="techno" src="stack/docker.svg" alt="docker" />
                    </div>
                </div>
            </div>
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
        color: #000;
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
        background: url("flags/france.svg");
        background-size: contain;
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
    }

    .contact-icon {
        width: 36px;
        height: 36px;
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

    .interests {
        display: flex;
        justify-content: center;
        align-items: center;
        flex-wrap: wrap;
    }

    .interest-icon {
        width: 45px;
        height: 45px;
    }

    .header {
        /* background: var(--color-black); */
        background: url("bordeaux.jpg");
        background-size: cover;
        background-position: center 55%;
        width: 100%;
        height: calc((var(--aside-width) / 2) + var(--padding));
    }

    .body {
        color: #fff;
        background: var(--color-dark);
        width: 100%;
        flex: 1;
        padding-block: var(--padding);
        padding-inline: calc(2 * var(--padding) + var(--aside-width)) var(--padding);
        display: flex;
        flex-direction: column;
        gap: 8mm;
    }

    .separator-line {
        background-color: var(--color-gold);
        width: 100%;
        height: 1px;
        margin-top: 2mm;
    }

    .title {
        color: var(--color-gold);
        font-size: 20px;
        text-transform: uppercase;
    }

    .timeline {
        display: flex;
        flex-direction: column;
        font-size: 16px;
    }

    .event {
        display: flex;
        gap: 8mm;
    }

    .line {
        background-color: var(--color-gold);
        position: relative;
        width: 2px;
        height: 100%;
    }

    .point {
        background-color: var(--color-dark);
        position: relative;
        left: -8px;
        width: 17px;
        height: 17px;
        border: 2px solid var(--color-gold);
        border-radius: 100%;
        box-sizing: border-box;
    }

    .description {
        flex: 1;
        display: flex;
        flex-direction: column;
        gap: 2mm;
    }

    .date {
        min-width: 25mm;
        display: flex;
        flex-direction: column;
        flex-wrap: wrap;
        align-items: flex-end;
        gap: 2mm;
        font-size: 16px;
    }

    ul {
        list-style-position: outside;
    }

    .star {
        width: 20px;
        height: 20px;
    }

    .techno {
        width: 55px;
        height: 55px;
    }
</style>
