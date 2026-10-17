<!-- LOVABLE:BEGIN -->
> [!IMPORTANT]
> This project is connected to [Lovable](https://lovable.dev). Avoid rewriting
> published git history — force pushing, or rebasing/amending/squashing commits
> that are already pushed — as it rewrites history on Lovable's side and the
> user will likely lose their project history.
>
> Commits you push to the connected branch sync back to Lovable and show up in
> the editor, so keep the branch in a working state.
<!-- LOVABLE:END -->

- Multi-restaurant: every product/invoice/image belongs to a restaurant (restaurant_id); lojistas are linked via restaurant_members and RLS (is_member) isolates data, because tenant separation must hold in the backend.
- Super-admin = user_roles 'admin'; public signup is disabled and lojista accounts are created by server functions in src/lib/contas.functions.ts, because only the platform may create accounts.
- Plan limits and protected restaurant fields (status, plan, slug, deleted_at) are enforced by database triggers, not the UI.
- Images go to the private "imagens" bucket under <restaurant_id>/ with long-lived signed URLs, because public buckets are blocked.
- Public store pages live at /r/$slug and render src/components/Loja.tsx; suspended stores show an unavailable notice.
