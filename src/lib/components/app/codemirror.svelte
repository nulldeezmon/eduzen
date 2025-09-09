<script lang="ts">
  import CodeMirror from "svelte-codemirror-editor";
  import { javascript } from "@codemirror/lang-javascript";
  import { html } from "@codemirror/lang-html";
  import { css } from "@codemirror/lang-css";
  import { python } from "@codemirror/lang-python";
  import { markdown } from "@codemirror/lang-markdown";
  import { json } from "@codemirror/lang-json";
  import { githubLight, githubDark } from "@uiw/codemirror-theme-github";
  import { mode } from "mode-watcher";

  const ext2lang: Record<string, Function> = {
    js: javascript,
    jsx: javascript,
    ts: javascript,
    tsx: javascript,
    json: json,
    json5: json,
    md: markdown,
    py: python,
    html: html,
    html5: html,
    css: css,
    scss: css,
  };

  function getFileExtension(filePath: string): string {
    const parts = filePath.split(".");
    if (parts.length > 1) {
      return parts.pop()?.toLowerCase() || "";
    }
    return "";
  }

  let { path = "", value = $bindable() } = $props();
  let ext = getFileExtension(path);
  const language: Function | null = ext2lang[ext] || null;

  let colorscheme = mode.current === "light" ? githubLight : githubDark;
</script>

{#if language}
  <CodeMirror bind:value lang={language()} theme={colorscheme} />
{:else}
  <CodeMirror bind:value theme={colorscheme} />
{/if}

<style>
</style>
