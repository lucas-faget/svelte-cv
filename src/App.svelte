<script lang="ts">
    import './app.css';
    import jsonData from './data.json';

    const ASSETS_FLAG = "/flag/";
    const ASSETS_ICON = "/icon/";
    const ASSETS_LOGO = "/logo/";

    $: pictureBackground = `background: url("/${jsonData.profileImage}"); background-size: cover;`;
    $: bannerBackground = `background: url("/${jsonData.bannerImage}"); background-size: cover; background-position: center 50%;`;
</script>

<main>
    {#if jsonData}
        <div id="cv">
            <div class="aside">
                <div class="picture" style={pictureBackground}></div>
                <div class="flex flex-column text-center" style="font-size: 40px;">
                    <span class="text-bold">{jsonData.firstName}</span>
                    <span>{jsonData.lastName}</span>
                </div>
                <div class="flex flex-column text-center" style="font-size: 20px;">
                    <span class="text-bold">{jsonData.position}</span>
                </div>
                <div class="flex flex-column" style="gap: 4mm;">
                    <div class="contact">
                        <img class="contact-icon" src={ASSETS_ICON + "website.svg"} alt="website" />
                        <span>{jsonData.website}</span>
                    </div>
                    <div class="contact">
                        <img class="contact-icon" src={ASSETS_ICON + "github.svg"} alt="github" />
                        <span>{jsonData.gitProfileUrl}</span>
                    </div>
                    <div class="contact">
                        <img class="contact-icon" src={ASSETS_ICON + "mail.svg"} alt="mail" />
                        <span>{jsonData.email}</span>
                    </div>
                    <div class="contact">
                        <img class="contact-icon" src={ASSETS_ICON + "phone.svg"} alt="phone" />
                        <span>{jsonData.phoneNumber}</span>
                    </div>
                </div>

                {#if jsonData.flags}
                    <div class="flags">
                        {#each jsonData.flags as flag}
                                <img class="flag" src={ASSETS_FLAG + flag} alt="flag" />
                        {/each}
                    </div>
                {/if}

                {#if jsonData.interests}
                    <div class="flex flex-column" style="gap: 4mm;">
                        <span class="text-center text-uppercase" style="font-size: 25px;">Intérêts</span>
                        <div class="interests" style="gap: 2mm;">
                            {#each jsonData.interests as interest}
                                <img class="interest-icon" src={ASSETS_ICON + interest.imageName} alt={interest.name} />
                            {/each}
                        </div>
                    </div>
                {/if}
            </div>

            <div class="header" style={bannerBackground}></div>
            <div class="body">
                {#each jsonData.sections as section}
                    <div class="flex flex-column">
                        <span class="title">{section.sectionTitle}</span>
                        <div class="separator-line"></div>
                    </div>
                    {#if section.events}
                        <div class="timeline">
                            {#each section.events as event, index}
                                <div class="event">
                                    <div class="date">
                                        <span>{event.date}</span>
                                    </div>
                                    <div class="line">
                                        <div class="point"></div>
                                    </div>
                                    <div class="description" style="gap: 2mm; {index !== section.events.length - 1 ? 'padding-bottom: 8mm;' : ''}">
                                        <span class="color-gold">{event.title}</span>
                                        <span class="color-gray" style="font-size: 14px;">{event.place}</span>
                                        {#if event.textList}
                                            <ul style="font-size: 14px;">
                                                {#each event.textList as text}
                                                    <li>{text}</li>
                                                {/each}
                                            </ul>
                                        {/if}
                                    </div>
                                </div>
                            {/each}
                        </div>
                    {/if}
                {/each}

                {#if jsonData.skills}
                    <div class="flex flex-column">
                        <span class="title">Technos</span>
                        <div class="separator-line"></div>
                    </div>
                    <!-- Stack -->
                    <div class="flex flex-column" style="gap: 8mm;">
                        {#if jsonData.skills.threeStarRatedSkills}
                            <div class="flex align-center" style="gap: 8mm;">
                                <div class="flex" style="gap: 2mm;">
                                    <img class="star" src={ASSETS_ICON + "gold-star.svg"} alt="star" />
                                    <img class="star" src={ASSETS_ICON + "gold-star.svg"} alt="star" />
                                    <img class="star" src={ASSETS_ICON + "gold-star.svg"} alt="star" />
                                </div>
                                <div class="flex" style="gap: 4mm;">
                                    {#each jsonData.skills.threeStarRatedSkills as skill}
                                        <img class="image" src={ASSETS_LOGO + skill.imageName} alt={skill.name} />
                                    {/each}
                                </div>
                            </div>
                        {/if}
                        {#if jsonData.skills.twoStarRatedSkills}
                            <div class="flex align-center" style="gap: 8mm;">
                                <div class="flex" style="gap: 2mm;">
                                    <img class="star" src={ASSETS_ICON + "gold-star.svg"} alt="star" />
                                    <img class="star" src={ASSETS_ICON + "gold-star.svg"} alt="star" />
                                    <img class="star" src={ASSETS_ICON + "black-star.svg"} alt="star" />
                                </div>
                                <div class="flex" style="gap: 4mm;">
                                    {#each jsonData.skills.twoStarRatedSkills as skill}
                                        <img class="image" src={ASSETS_LOGO + skill.imageName} alt={skill.name} />
                                    {/each}
                                </div>
                            </div>
                        {/if}
                        {#if jsonData.skills.oneStarRatedSkills}
                            <div class="flex align-center" style="gap: 8mm;">
                                <div class="flex" style="gap: 2mm;">
                                    <img class="star" src={ASSETS_ICON + "gold-star.svg"} alt="star" />
                                    <img class="star" src={ASSETS_ICON + "black-star.svg"} alt="star" />
                                    <img class="star" src={ASSETS_ICON + "black-star.svg"} alt="star" />
                                </div>
                                <div class="flex" style="gap: 4mm;">
                                    {#each jsonData.skills.oneStarRatedSkills as skill}
                                        <img class="image" src={ASSETS_LOGO + skill.imageName} alt={skill.name} />
                                    {/each}
                                </div>
                            </div>
                        {/if}
                    </div>
                {/if}
            </div>
        </div>
    {/if}
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
    }

    #cv {
        position: relative;
        width: 210mm;
        height: 297mm;
        display: flex;
        flex-direction: column;
        font-family: 'Roboto';
    }

    @media print {
        #cv {
            position: absolute;
            left: 0;
            top: 0;
        }
        @page {
            size: A4;
            margin: 0;
        }
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
        display: flex;
        flex-direction: column;
        gap: 2mm;
    }

    .star {
        width: 20px;
        height: 20px;
    }

    .image {
        height: 55px;
        min-width: 55px;
        max-width: 80px;
    }
</style>
