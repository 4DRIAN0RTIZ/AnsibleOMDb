# OMDb API to Excel - Ansible Playbook

Queries the OMDb API and creates an Excel file with movie search results.

## Prerequisites

- Ansible
- Python 3
- OMDb API key

## Setup

1. Create the secrets file:
   ```bash
   cp vars/secrets.yml.example vars/secrets.yml
   ```

2. Edit `vars/secrets.yml` with your API key:
   ```yaml
   ---
   omdb_api_key: "your-api-key-here"
   ```

2.1 Decrypt the secrets file if using Ansible Vault:
   ```bash
   ansible-vault decrypt vars/secrets.yml
   ```

## Variables

### Secrets (vars/secrets.yml)
- `omdb_api_key`: Your OMDb API key (required)

### Playbook Variables (api_to_excel.yml)
Edit these directly in the playbook:

```yaml
vars:
  search_term: "Matrix"
  output_file: "movies_results.xlsx"
```

You can also override variables when running:
```bash
ansible-playbook api_to_excel.yml -e "search_term=Batman"
```

## Usage

Run the playbook:
```bash
ansible-playbook api_to_excel.yml
```

The Excel file will be created with columns: Title, Year, IMDb ID, Type, Poster URL.

## Logs

Playbook execution logs are saved to `ansible_api_excel.log`.

See [LOG_FORMAT.md](LOG_FORMAT.md) for log format details.
