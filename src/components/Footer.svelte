<script>
    import { invoke } from "@tauri-apps/api/tauri"

    let current_year = new Date().getFullYear();
    let author_name = "";
    let github_repository_link = "";

    (async () => {
        author_name = await invoke("get_author_name")
        github_repository_link = await invoke("get_repository_link")
    })().catch(err => {
        console.error(err);
    });
</script>

<footer id="footer">
    <p>© {current_year} Все права защищены.</p>
</footer>

<style lang="scss">
  #footer {
    text-align: center;
    color: #565759;
    font-size: 12px;
    font-weight: bold;
    line-height: 1.7em;
    margin-top: 15px;
    position: fixed;
    bottom: 0;
    left: 0;
    width: 100%;

  p {
  margin: 0;
  padding: 0;
  }

  a {
  color: #185876;
  text-decoration: none;

  &:hover {
                color: #2A9CD0;
            }
        }
    }
</style>