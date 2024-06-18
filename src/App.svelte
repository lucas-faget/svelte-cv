<script lang="ts">
    import "./app.css";
    import jsonData from "/data.json";

    $: pictureBackground = `background: url("${jsonData.profileImageUrl}"); background-size: cover; background-position: center 45%;`;
    $: bannerBackground = `background: url("${jsonData.bannerImageUrl}"); background-size: cover; background-position: center 50%;`;
</script>

<main>
    {#if jsonData}
        <div id="cv">
            <div class="aside">
                <div class="picture" style={pictureBackground}></div>
                <div class="flex flex-column" style="gap: 4mm;">
                    <div class="contact">
                        <img
                            class="contact-icon"
                            src="http://assets.lucas-faget.com/icons/collections/elegant-circle/global.svg"
                            alt="website"
                        />
                        <span>{jsonData.websiteUrl}</span>
                    </div>
                    <div class="contact">
                        <img
                            class="contact-icon"
                            src="http://assets.lucas-faget.com/logos/github.svg"
                            alt="github"
                        />
                        <span>{jsonData.gitProfileUrl}</span>
                    </div>
                    <div class="contact">
                        <img
                            class="contact-icon"
                            src="http://assets.lucas-faget.com/logos/linkedin.svg"
                            alt="linkedin"
                        />
                        <span>{jsonData.linkedinProfileUrl}</span>
                    </div>
                    <div class="contact">
                        <img
                            class="contact-icon"
                            src="http://assets.lucas-faget.com/icons/collections/elegant-circle/mail.svg"
                            alt="mail"
                        />
                        <span>{jsonData.email}</span>
                    </div>
                    <div class="contact">
                        <img
                            class="contact-icon"
                            src="http://assets.lucas-faget.com/icons/collections/elegant-circle/phone.svg"
                            alt="phone"
                        />
                        <span>{jsonData.phoneNumber}</span>
                    </div>
                </div>

                {#if jsonData.flags}
                    <div class="flex flex-column" style="gap: 4mm;">
                        <span class="text-center text-uppercase" style="font-size: 25px;"
                            >Langues</span
                        >
                        <div class="flags">
                            {#each jsonData.flags as flag}
                                <img
                                    class="flag"
                                    src={`http://assets.lucas-faget.com/icons/flag-${flag}-circle`}
                                    alt="flag"
                                />
                            {/each}
                        </div>
                    </div>
                {/if}

                {#if jsonData.interests}
                    <div class="flex flex-column" style="gap: 4mm;">
                        <span class="text-center text-uppercase" style="font-size: 25px;"
                            >Intérêts</span
                        >
                        <div class="interests" style="gap: 2mm;">
                            {#each jsonData.interests as interest}
                                <img
                                    class="interest-icon"
                                    src={interest.imageUrl}
                                    alt={interest.name}
                                />
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
                                    <div
                                        class="description"
                                        style="gap: 2mm; {index !== section.events.length - 1
                                            ? 'padding-bottom: 8mm;'
                                            : ''}"
                                    >
                                        <span class="color-primary">{event.title}</span>
                                        <span class="color-gray" style="font-size: 14px;"
                                            >{event.place}</span
                                        >
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
                    <div class="grid">
                        {#if jsonData.skills.frontend}
                            <div class="flex align-center text-no-wrap">Front-end :</div>
                            <div class="flex" style="gap: 4mm;">
                                {#each jsonData.skills.frontend as skill}
                                    <img class="image" src={skill.imageUrl} alt={skill.name} />
                                {/each}
                            </div>
                        {/if}
                        {#if jsonData.skills.backend}
                            <div class="flex align-center text-no-wrap">Back-end :</div>
                            <div class="flex" style="gap: 4mm;">
                                {#each jsonData.skills.backend as skill}
                                    <img class="image" src={skill.imageUrl} alt={skill.name} />
                                {/each}
                            </div>
                        {/if}
                        {#if jsonData.skills.otherTools}
                            <div class="flex align-center text-no-wrap">Autres :</div>
                            <div class="flex" style="gap: 4mm;">
                                {#each jsonData.skills.otherTools as skill}
                                    <img class="image" src={skill.imageUrl} alt={skill.name} />
                                {/each}
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
        --aside-text-color: var(--color-dark);
        --aside-background-color: var(--color-gold-light);

        --body-title-color: var(--color-primary);
        --body-text-color: var(--color-dark);
        --body-background-color: var(--color-white);

        --cv-width: 210mm;
        --cv-height: 297mm;

        --padding: 8mm;

        --aside-width: 63mm;
        --aside-padding: 4mm;
    }

    .color-gray {
        color: var(--color-gray);
    }

    .color-primary {
        color: var(--color-primary);
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
        color: var(--aside-text-color);
        background: var(--aside-background-color);
        position: absolute;
        top: var(--padding);
        left: var(--padding);
        width: var(--aside-width);
        height: calc(var(--cv-height) - 2 * var(--padding));
        border-radius: var(--aside-width);
        display: flex;
        flex-direction: column;
        gap: 8mm;
    }

    .picture {
        width: calc(var(--aside-width) - 2 * var(--aside-padding));
        height: calc(var(--aside-width) - 2 * var(--aside-padding));
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
        color: var(--body-text-color);
        background: var(--body-background-color);
        width: 100%;
        flex: 1;
        padding-block: var(--padding);
        padding-inline: calc(2 * var(--padding) + var(--aside-width)) var(--padding);
        display: flex;
        flex-direction: column;
        gap: 8mm;
    }

    .separator-line {
        background-color: var(--body-title-color);
        width: 100%;
        height: 0.5px;
    }

    .title {
        color: var(--body-title-color);
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
        background-color: var(--body-title-color);
        position: relative;
        width: 1px;
        height: 100%;
    }

    .point {
        background-color: var(--body-background-color);
        position: relative;
        left: 1px;
        transform: translateX(-50%);
        width: 20px;
        aspect-ratio: 1/1;
        border: 1px solid var(--body-title-color);
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

    .image {
        height: 55px;
        min-width: 55px;
        max-width: 80px;
    }

    .grid {
        display: grid;
        grid-template-columns: minmax(auto, max-content) 1fr;
        grid-template-rows: repeat(3, 1fr);
        grid-gap: 8mm;
    }
</style>
