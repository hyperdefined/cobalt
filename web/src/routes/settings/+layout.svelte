<script lang="ts">
    import settings from "$lib/state/settings";

    import { version } from "$lib/version";
    import { t } from "$lib/i18n/translations";

    import PageNav from "$components/subnav/PageNav.svelte";

    import PageNavTab from "$components/subnav/PageNavTab.svelte";
    import PageNavSection from "$components/subnav/PageNavSection.svelte";

    import { IconLock } from "@tabler/icons-svelte";
    import { IconSunHigh } from "@tabler/icons-svelte";
    import { IconAccessible } from "@tabler/icons-svelte";

    import { IconMovie } from "@tabler/icons-svelte";
    import { IconMusic } from "@tabler/icons-svelte";
    import { IconFileDownload } from "@tabler/icons-svelte";

    import { IconCpu } from "@tabler/icons-svelte";
    import { IconWorld } from "@tabler/icons-svelte";

    import { IconBug } from "@tabler/icons-svelte";
    import { IconAdjustmentsStar } from "@tabler/icons-svelte";

    $: versionText = $version
        ? `v${$version.version}-${$version.commit.slice(0, 8)}`
        : "\xa0";
</script>

<PageNav
    pageName="settings"
    pageSubtitle={versionText}
    homeNavPath="/settings"
    homeTitle={$t("tabs.settings")}
>
    <svelte:fragment slot="navigation">
        <PageNavSection>
            <PageNavTab
                path="/settings/appearance"
                title={$t("settings.page.appearance")}
                icon={IconSunHigh}
                iconColor="blue"
            />
            <PageNavTab
                path="/settings/accessibility"
                title={$t("settings.page.accessibility")}
                icon={IconAccessible}
                iconColor="purple"
            />
        </PageNavSection>

        <PageNavSection>
            <PageNavTab
                path="/settings/video"
                title={$t("settings.page.video")}
                icon={IconMovie}
                iconColor="magenta"
            />
            <PageNavTab
                path="/settings/audio"
                title={$t("settings.page.audio")}
                icon={IconMusic}
                iconColor="orange"
            />
            <PageNavTab
                path="/settings/metadata"
                title={$t("settings.page.metadata")}
                icon={IconFileDownload}
                iconColor="green"
            />
        </PageNavSection>

        <PageNavSection>
            <PageNavTab
                path="/settings/local"
                title={$t("settings.page.local")}
                icon={IconCpu}
                iconColor="blue"
            />
            <PageNavTab
                path="/settings/instances"
                title={$t("settings.page.instances")}
                icon={IconWorld}
                iconColor="purple"
            />
        </PageNavSection>

        <PageNavSection>
            <PageNavTab
                path="/settings/privacy"
                title={$t("settings.page.privacy")}
                icon={IconLock}
                iconColor="gray"
            />
            <PageNavTab
                path="/settings/advanced"
                title={$t("settings.page.advanced")}
                icon={IconAdjustmentsStar}
            />
            {#if $settings.advanced.debug}
                <PageNavTab
                    path="/settings/debug"
                    title={$t("settings.page.debug")}
                    icon={IconBug}
                />
            {/if}
        </PageNavSection>
    </svelte:fragment>

    <slot slot="content"></slot>
</PageNav>
