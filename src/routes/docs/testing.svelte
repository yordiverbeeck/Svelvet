<script>
</script>

<div>
  <h2 class="text-4xl font-semibold mb-12">Testing</h2>
  <h3 class="text-xl font-semibold">External</h3>

  <p class="my-4 text-gray-600">
    While testing your application, it is highly recommended to exclude Svelvet components as best
    you can. A library that has a fantastic API for UI-centric testing is
    <a
      class="text-rose-600 underline underline-offset-1"
      target="_blank"
      href="https://testing-library.com/docs/svelte-testing-library/intro/"
      >@testing-library/svelte</a
    >.
  </p>
  <p class="my-4 text-gray-600">
    For example, when rendering the Svelvet component, your test could query for the contents rather
    than the specific Svelvet instance. Svelvet undergoes frequent version updates, and by not
    relying on the Svelte component tree you make your test more robust against internal changes in
    Svelvet.
  </p>

  <p class="my-4 text-gray-600">
    <strong>For SvelteKit apps:</strong> While
    <a class="text-rose-600 underline underline-offset-1" target="_blank" href="https://jestjs.io/"
      >@jest</a
    >
    is a reliable option for running your tests, SvelteKit applications are built with Vite and thus
    require separate configurations. We found that
    <a class="text-rose-600 underline underline-offset-1" target="_blank" href="https://vitest.dev/"
      >@vitest</a
    >
    is a great option for Vite apps as they share the same config files and require little additional
    work to get started, letting you focus on writing quality tests rather than config issues.
  </p>
</div>
<div>
  <h3 class="text-xl font-semibold mt-12">Internal</h3>
  <p class="my-4 text-gray-600">
    Svelvet components are built with unit, integration and end-to-end tests using <a
      class="text-rose-600 underline underline-offset-1"
      target="_blank"
      href="https://vitest.dev/">@vitest</a
    >,
    <a
      class="text-rose-600 underline underline-offset-1"
      target="_blank"
      href="https://testing-library.com/docs/svelte-testing-library/intro/"
      >@testing-library/svelte</a
    >, and
    <a
      class="text-rose-600 underline underline-offset-1"
      target="_blank"
      href="https://www.cypress.io/">@cypress</a
    > along with an integrated CI/CD pipeline. Therefore, package version updates and usage could be
    done with confidence.
  </p>
</div>
