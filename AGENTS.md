# Repository guide

## Map and legacy environment

This branch is a Rails 3 CMS engine with a runnable host application. `app/models/cms/`, `app/controllers/`, and `app/views/` hold CMS behavior; `app/assets/` contains editor/UI assets; `lib/` holds engine utilities and generators; `db/` and `test/` hold schema/fixtures and tests.

Install with `bundle install` in a compatible historical Ruby/Rails environment. `.travis.yml` tests Ruby 1.8.7/1.9.x and Rails 3.0/3.1/3.2 Gemfiles under `test/gemfiles/`; those are compatibility targets, not proof they work on a current host. SQLite and Paperclip's image-processing prerequisites may be needed. For matrix reproduction, select the relevant `BUNDLE_GEMFILE` consistently at install and test time. No separate lint command or lockfile is tracked.

Use `bundle exec rake test` for Rails tests and `bundle exec rails server` for local UI work after preparing only the disposable local database. `config/database.yml` warns that tests erase/recreate the test database; never substitute shared/production data. Follow the generated gemspec header: edit gem metadata through the Jeweler task in `Rakefile`, then `rake gemspec`, rather than editing the generated gemspec directly.

## Completion and boundaries

Preserve authentication, site isolation, revision history, and fixture semantics. Do not expose the default demo admin login on a public server. Start with `git status --short`, preserve unrelated changes, and carry authorized implementation through focused tests and repairs; inspect rendered admin/content flows for UI changes. Routine reversible choices do not need extra approval. Live migrations, publishing content, deployment, and gem releases require explicit authorization.

For prose-only edits, check paths/links and run `git diff --check`. Report the exact legacy dependency/database blocker, keep doing independent work, and close with changed paths, actual checks/results, and remaining browser/integration gaps.
