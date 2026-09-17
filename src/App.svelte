<script lang="ts">
	let currentPage = 'home';
  let password = '';
  let passwordError = '';

  function unlockArchive() {
    if (password === 'ꕪꔤꔖꖩꕪꗳꖨ') {
      password = '';
      passwordError = '';
      currentPage = 'restricted';
    } else {
      passwordError = 'Access denied.';
    }
  }

	const navigation = [
		{ id: 'home', label: 'Home' },
		{ id: 'sources', label: 'Sources' },
		{ id: 'articles', label: 'Articles' },
		{ id: 'about', label: 'About this archive' }
	];

	const sources = [
		{
			id: 'SRN-001',
			title: 'The Song of the Chorus',
			type: 'Primary text',
			status: 'Incomplete'
		},
		{
			id: 'SRN-002',
			title: 'The Chorus and the Muses',
			type: 'Translated fragment',
			status: 'Reviewed'
		},
		{
			id: 'SRN-003',
			title: 'Orphée and the Chorus',
			type: 'Translated fragment',
			status: 'Reviewed'
		},
		{
			id: 'SRN-004',
			title: 'The Search of Persephone',
			type: 'Translated fragment',
			status: 'Unclassified'
		}
	];

	const articles = [
		{
			id: 'article-chorus',
			date: '02/06/31',
			category: 'Research / Mythology',
			title: 'The Chorus: A Study of an Obscure Sairen Myth'
		},
		{
			id: 'article-orphee',
			date: '17/16/30',
			category: 'Sources / Linguistics',
			title: 'Notes on the name "Orphée"'
		}
	];

	function navigate(page: string) {
		currentPage = page;
	}
</script>

<svelte:head>
	<title>Sairen Studies — Independent Archive</title>

	<meta
		name="description"
		content="An independent archive concerning Sairen mythology, history and related sources."
	/>
</svelte:head>

<div class="site">

	<!-- =====================================================
	     HEADER
	     ===================================================== -->

	<header class="header">
		<div class="header-top">

			<div>
				<h1>SAIREN STUDIES</h1>

				<p>
					Independent archive of Sairen mythology and related sources
				</p>
			</div>

			<div class="status">
				ARCHIVE STATUS: <strong>OPEN</strong><br />
				Last updated: 02/06/31
			</div>

		</div>

		<nav class="navigation">

			{#each navigation as item}

				<a
					href="/"
					class:active={currentPage === item.id}
					on:click|preventDefault={() => navigate(item.id)}
				>
					{item.label}
				</a>

			{/each}

		</nav>
	</header>


	<!-- =====================================================
	     LAYOUT
	     ===================================================== -->

	<div class="layout">

		<!-- =================================================
		     SIDEBAR
		     ================================================= -->

		<aside class="sidebar">

			<section class="panel">

				<h2>ARCHIVE</h2>

				<ul>

					<li>
						<a
							href="/"
							on:click|preventDefault={() => navigate('sources')}
						>
							Sources
						</a>
					</li>

					<li>
						<a
							href="/"
							on:click|preventDefault={() => navigate('articles')}
						>
							Articles
						</a>
					</li>
          <li>
            <a
              href="https://www.lexilogos.com/keyboard/vai.htm"
              target="_blank"
              rel="noreferrer"
            >
              Sairen Dialect
            </a>
          </li>

				</ul>

			</section>


			<section class="panel">

				<h2>RECENT FILES</h2>

				<ul>

					<li>
						<a
							href="/"
							on:click|preventDefault={() => navigate('source-SRN-004')}
						>
							SRN-004
						</a>

						<span>Persephone</span>
					</li>

					<li>
						<a
							href="/"
							on:click|preventDefault={() => navigate('source-SRN-003')}
						>
							SRN-003
						</a>

						<span>Orphée</span>
					</li>

					<li>
						<a
							href="/"
							on:click|preventDefault={() => navigate('source-SRN-002')}
						>
							SRN-002
						</a>

						<span>The Muses</span>
					</li>

					<li>
						<a
							href="/"
							on:click|preventDefault={() => navigate('source-SRN-001')}
						>
							SRN-001
						</a>

						<span>The Chorus</span>
					</li>

				</ul>

			</section>


			<section class="panel small">

				<h2>NOTICE</h2>

				<p>
					This archive is an independent research project.
					Translations are provided for research purposes.
				</p>

				<p>
					Some source material remains incomplete or uncertain.
				</p>

			</section>
      <section class="panel small">
        <h2>RESTRICTED</h2>

        <p>
          Some archived material is not currently available to the public.
        </p>

        <form on:submit|preventDefault={unlockArchive}>

          <label for="archive-password">
            Archive password:
          </label>

          <input
            id="archive-password"
            type="password"
            bind:value={password}
            autocomplete="off"
          />

          <button type="submit">
            Enter
          </button>

        </form>

        {#if passwordError}
          <p class="password-error">
            {passwordError}
          </p>
        {/if}

      </section>

		</aside>


		<!-- =================================================
		     MAIN CONTENT
		     ================================================= -->

		<main class="content">


			<!-- =================================================
			     HOME
			     ================================================= -->

			{#if currentPage === 'home'}

				<section class="intro">

					<h2>The Chorus</h2>

					<p class="subtitle">
						An obscure Sairen myth concerning three singers,
						a forgotten world, and a figure known only as Orphée.
					</p>

					<p>
            This website collects translated fragments, references
            and research notes concerning a small group of texts
            apparently describing the same Sairen legend, sometimes
            referred to collectively as the
            <a
              href="https://youtu.be/P4S7EaXozXw"
              target="_blank"
              rel="noreferrer"
            >
              Chorus
            </a>.
          </p>

					<p>
						The sources are difficult to date and disagree on several
						important details. Names, places and even the number of
						Sirens described in older versions vary considerably.
					</p>

					<p>
						The purpose of this archive is not to establish a single
						interpretation, but to collect the available material
						and document possible connections between the sources.
					</p>

				</section>


				<section class="section">

					<div class="section-header">
						<h2>Latest additions</h2>

						<a
							href="/"
							on:click|preventDefault={() => navigate('sources')}
						>
							[view all]
						</a>
					</div>


					<table class="source-table">

						<thead>

							<tr>
								<th>Source ID</th>
								<th>Title</th>
								<th>Type</th>
								<th>Status</th>
							</tr>

						</thead>


						<tbody>

							{#each [...sources].reverse() as source}

								<tr>

									<td>{source.id}</td>

									<td>
										<a
											href="/"
											on:click|preventDefault={() =>
												navigate('source-' + source.id)
											}
										>
											{source.title}
										</a>
									</td>

									<td>{source.type}</td>

									<td>{source.status}</td>

								</tr>

							{/each}

						</tbody>

					</table>

				</section>


				<section class="section">

					<div class="section-header">

						<h2>Research notes</h2>

						<a
							href="/"
							on:click|preventDefault={() => navigate('articles')}
						>
							[archive]
						</a>

					</div>


					{#each articles as article}

						<article class="post">

							<h3>

								<a
									href="/"
									on:click|preventDefault={() => navigate(article.id)}
								>
									{article.title}
								</a>

							</h3>

							<div class="post-meta">
								Posted {article.date} — {article.category}
							</div>

							<p>

								{#if article.id === 'article-chorus'}

									The three figures described in the oldest
									available fragment may correspond to several
									later traditions concerning Sirens. Their
									relationship to Persephone, however, remains
									unclear.

								{:else}

									The name does not appear to correspond
									directly to the name of a known Sairen ruler.
									It may instead be a translated title or epithet.

								{/if}

							</p>

							<a
								href="/"
								on:click|preventDefault={() => navigate(article.id)}
							>
								Continue reading...
							</a>

						</article>

					{/each}

				</section>


				<section class="section warning">

					<h2>A note concerning the sources</h2>

					<p>
						Several texts contained in this archive were recovered
						from secondary publications rather than original
						manuscripts.
					</p>

					<p>
						Names and passages which could not be reliably translated
						have been marked accordingly.
					</p>

					<p>
						<strong>
							Source material should not be treated as historical
							evidence without further verification.
						</strong>
					</p>

				</section>


			<!-- =================================================
			     SOURCES INDEX
			     ================================================= -->

			{:else if currentPage === 'sources'}

				<section class="intro">

					<h2>Sources</h2>

					<p class="subtitle">
						Collected texts and fragments concerning Sairen mythology.
					</p>

					<p>
						This section contains the texts currently available
						in the archive. Most entries are translations or
						transcriptions of material found in secondary
						publications.
					</p>

					<p>
						Source classification is provisional and may be revised
						as additional material becomes available.
					</p>

				</section>


				<section class="section">

					<div class="section-header">

						<h2>Source index</h2>

						<span>4 records</span>

					</div>


					<table class="source-table">

						<thead>

							<tr>
								<th>Source ID</th>
								<th>Title</th>
								<th>Type</th>
								<th>Status</th>
							</tr>

						</thead>


						<tbody>

							{#each sources as source}

								<tr>

									<td>{source.id}</td>

									<td>

										<a
											href="/"
											on:click|preventDefault={() =>
												navigate('source-' + source.id)
											}
										>
											{source.title}
										</a>

									</td>

									<td>{source.type}</td>

									<td>{source.status}</td>

								</tr>

							{/each}

						</tbody>

					</table>

				</section>


				<section class="section">

					<div class="section-header">
						<h2>Classification</h2>
					</div>

					<p>
						<strong>Primary text</strong> indicates material for
						which the archive currently possesses a direct
						transcription or translation.
					</p>

					<p>
						<strong>Translated fragment</strong> indicates material
						preserved through another publication or translation.
					</p>

					<p>
						<strong>Unclassified</strong> indicates that the
						provenance or date of the material remains uncertain.
					</p>

				</section>


			<!-- =================================================
			     SRN-001
			     ================================================= -->

			{:else if currentPage === 'source-SRN-001'}

				<section class="intro">

					<h2>The Song of the Chorus</h2>

					<p class="subtitle">
						SRN-001 — Primary text
					</p>

					<table class="source-table source-info">

						<tbody>

							<tr>
								<th>Source ID</th>
								<td>SRN-001</td>
							</tr>

							<tr>
								<th>Classification</th>
								<td>Primary text</td>
							</tr>

							<tr>
								<th>Date</th>
								<td>Unknown</td>
							</tr>

							<tr>
								<th>Language</th>
								<td>Sairen</td>
							</tr>

							<tr>
								<th>Translation</th>
								<td>Anonymous</td>
							</tr>

							<tr>
								<th>Status</th>
								<td>Incomplete</td>
							</tr>

						</tbody>

					</table>

				</section>

        <section class="section source-text">

          <div class="section-header">
            <h2>Translated text</h2>
          </div>

          <p>
            In the first days, when the songs of the Sairens were still young,
            there were three who sang unlike any others.
          </p>

          <p>
            They were sisters, though no mother is named for them, and no egg is
            said to have hatched them. They were simply there, as the sea is there
            and the sky is there. Their names were
            <span class="redacted">█████</span>,
            <span class="redacted">███████</span>, and
            <span class="redacted">█████████</span>.
            Together they were called the Chorus.
          </p>

          <p>
            The Chorus was blessed with voices of extraordinary beauty. Their songs
            could cross greater distances than those of other Sairens, and those
            who heard them found it difficult to think of anything else. Their
            songs could calm the frightened, excite the joyful, and make even the
            most watchful forget what they had been doing.
          </p>

          <p>
            But the Chorus did not use their voices for the good of the Sairen
            people. They sang for themselves.
          </p>

          <p>
            They taught that the strongest voice should command the weaker, that the
            most beautiful singer should be obeyed, and that those who could not
            resist a song had no right to complain of being led.
          </p>

          <p>
            The Chorus promised freedom. They promised that no Sairen would ever
            again have to obey another. Yet their freedom had only one condition:
            Everyone had to listen to them.
          </p>

          <p>
            Thus the Chorus travelled from settlement to settlement, singing to the
            young and the old, to soldiers and workers, to rulers and hatchlings.
            Wherever they went, Sairens gathered around them.
          </p>

          <p>
            Some followed willingly. Some followed because they could not bring
            themselves to leave. Others forgot, after hearing the Chorus, why they
            had ever opposed them. The three sisters began to believe that all
            Sairens would eventually become their chorus.
          </p>

          <p>
            But the Chorus had forgotten the oldest truth of the Sairen people:
            A voice exists to join the song, not to silence it.
          </p>

          <hr />

          <p>
            In those days there came a great ruler from beyond the stars. His name
            was <span class="redacted">██████ ███████</span> but the Chorus never
            called him by that name. They called him Orphée. Orphée did not fight
            the Chorus with weapons. He answered their song.
          </p>

          <p>
            Where the Chorus sang, his followers sang louder. Where the Chorus
            promised freedom, the followers of Orphée promised order. Where the
            Chorus called upon the individual, Orphée called upon the people.
          </p>

          <p>
            Those who followed Orphée became known to the Chorus as the Muses. The
            Chorus despised them.
          </p>

          <p>
            To the three sisters, the Muses were Sairens who had forgotten their own
            voices. They did not sing what they believed. They sang what they had
            been taught to sing.
          </p>

          <p>
            And so began the Great Contest of Voices. The Chorus and the Muses sang
            before the gathered Sairens.
          </p>

          <p>
            <span class="redacted">█████</span> sang of the endless sea.
          </p>

          <p>
            <span class="redacted">███████</span> sang of the peace found when every
            doubt disappears.
          </p>

          <p>
            <span class="redacted">█████████</span> sang of a world in which no voice
            can ever command another.
          </p>

          <p>
            The Muses answered with a different song. They sang of duty. They sang
            of unity. They sang of the Sairen people.
          </p>

          <p>
            And when the last note had faded, the gathered Sairens chose the song
            of the Muses.
          </p>

          <hr />

          <p>
            The punishment of the Chorus was terrible. The Muses stripped the three
            sisters of their feathers and made crowns from them, so that every
            Sairen might see what became of those who believed their own voices
            greater than the song of the people.
          </p>

          <p>
            The Chorus was then taken beneath the waters and imprisoned in a place
            whose name has been forgotten. There they were bound in silence. For
            the first time since the beginning of the world,
            <span class="redacted">█████</span>,
            <span class="redacted">███████</span>, and
            <span class="redacted">█████████</span> could not sing.
          </p>

          <p>
            The Muses believed this was the end. They were wrong, for before they
            were sealed away,
            <a
              href="https://youtu.be/Iqtaf7zTy_o"
              target="_blank"
              rel="noreferrer"
              class="redacted"
            >
              █████████
            </a>
            spoke a finalprophecy.
          </p>

          <p>
            “The song you have chosen is not your own. One day, when the Muses have
            forgotten why they sing, the Chorus will sing again. When we return, we
            will find Persephone.”
          </p>

          <p>
            No Sairen knows what Persephone was. The oldest songs do not explain,
            and the Sairens must never listen.
          </p>

          <p>
            For the Chorus does not sing to be heard, the Chorus sings to make you
            follow.
          </p>

        </section>


				<section class="section">

					<div class="section-header">
						<h2>Related sources</h2>
					</div>

					<ul>

						<li>
							<a
								href="/"
								on:click|preventDefault={() => navigate('source-SRN-002')}
							>
								SRN-002 — The Chorus and the Muses
							</a>
						</li>

						<li>
							<a
								href="/"
								on:click|preventDefault={() => navigate('source-SRN-003')}
							>
								SRN-003 — Orphée and the Chorus
							</a>
						</li>

						<li>
							<a
								href="/"
								on:click|preventDefault={() => navigate('source-SRN-004')}
							>
								SRN-004 — The Search of Persephone
							</a>
						</li>

					</ul>

				</section>


			<!-- =================================================
			     SRN-002
			     ================================================= -->

			{:else if currentPage === 'source-SRN-002'}

				<section class="intro">

					<h2>The Chorus and the Muses</h2>

					<p class="subtitle">
						SRN-002 — Translated fragment
					</p>

					<table class="source-table source-info">

						<tbody>

							<tr>
								<th>Source ID</th>
								<td>SRN-002</td>
							</tr>

							<tr>
								<th>Classification</th>
								<td>Translated fragment</td>
							</tr>

							<tr>
								<th>Original attribution</th>
								<td>Pausanias</td>
							</tr>

							<tr>
								<th>Status</th>
								<td>Reviewed</td>
							</tr>

						</tbody>

					</table>

				</section>


				<section class="section source-text">

					<div class="section-header">
						<h2>Translated text</h2>
					</div>

					<p>
						She has some Sirens in her hand. For they say that they,
						the daughters of Achelous, were persuaded by Hera to vie
						with the Muses in singing.
					</p>

					<p>
						The Muses being victorious plucked off their wings and
						made crowns of them.
					</p>

				</section>


				<section class="section">

					<div class="section-header">
						<h2>Researcher's note</h2>
					</div>

					<p>
						This passage is particularly interesting because it
						presents the Sirens and the Muses not as enemies in the
						usual sense, but as competitors in song.
					</p>

					<p>
						The removal of the wings may represent humiliation,
						punishment, or perhaps a symbolic loss of status.
						The original meaning is uncertain.
					</p>

				</section>


			<!-- =================================================
			     SRN-003
			     ================================================= -->

			{:else if currentPage === 'source-SRN-003'}

				<section class="intro">

					<h2>Orphée and the Chorus</h2>

					<p class="subtitle">
						SRN-003 — Translated fragment
					</p>

					<table class="source-table source-info">

						<tbody>

							<tr>
								<th>Source ID</th>
								<td>SRN-003</td>
							</tr>

							<tr>
								<th>Classification</th>
								<td>Translated fragment</td>
							</tr>

							<tr>
								<th>Original attribution</th>
								<td>Apollonius Rhodius</td>
							</tr>

							<tr>
								<th>Location</th>
								<td>Argonautica, Book IV</td>
							</tr>

							<tr>
								<th>Status</th>
								<td>Reviewed</td>
							</tr>

						</tbody>

					</table>

				</section>


				<section class="section source-text">

					<div class="section-header">
						<h2>Translated text</h2>
					</div>

					<p>
						And soon they saw a fair island, Anthemoessa, where the
						clear-voiced Sirens, daughters of Achelous, used to beguile
						with their sweet songs whoever cast anchor there, and then
						destroy him.
					</p>

					<p>
						They were once companions of Demeter's noble daughter,
						and sang to her in chorus.
					</p>

					<p>
						And they were already about to cast from the ship the
						hawsers to the shore, had not Thracian Orpheus, son of
						Oeagrus, stringing in his hands his Bistonian lyre, rung
						forth a hasty melody.
					</p>

					<p>
						The lyre overcame the maidens' voice.
					</p>

					<p>
						And the west wind and the sounding wave rushing astern
						bore the ship on; and the Sirens kept uttering their
						ceaseless song.
					</p>

				</section>


				<section class="section">

					<div class="section-header">
						<h2>Researcher's note</h2>
					</div>

					<p>
						The importance of Orpheus in this passage is unusual.
						He does not defeat the Sirens through violence, but
						through another form of music.
					</p>

					<p>
						This may be relevant when compared with the tradition
						in which the Chorus is defeated by another group of
						singers.
					</p>

				</section>


			<!-- =================================================
			     SRN-004
			     ================================================= -->

			{:else if currentPage === 'source-SRN-004'}

				<section class="intro">

					<h2>The Search of Persephone</h2>

					<p class="subtitle">
						SRN-004 — Translated fragment
					</p>

					<table class="source-table source-info">

						<tbody>

							<tr>
								<th>Source ID</th>
								<td>SRN-004</td>
							</tr>

							<tr>
								<th>Classification</th>
								<td>Translated fragment</td>
							</tr>

							<tr>
								<th>Original attribution</th>
								<td>Ovid</td>
							</tr>

							<tr>
								<th>Location</th>
								<td>Metamorphoses, Book V</td>
							</tr>

							<tr>
								<th>Status</th>
								<td>Unclassified</td>
							</tr>

						</tbody>

					</table>

				</section>


				<section class="section source-text">

					<div class="section-header">
						<h2>Translated text</h2>
					</div>

					<p>
						Why have you, Sirens, skilled in song, daughters of
						Acheloüs, the feathers and claws of birds, while still
						bearing human faces?
					</p>

					<p>
						Is it because you were numbered among the companions,
						when Proserpine gathered the flowers of Spring?
					</p>

					<p>
						When you had searched in vain for her on land, you
						wanted to cross the waves on beating wings, so that the
						waters might also know of your trouble.
					</p>

					<p>
						The gods were willing, and suddenly you saw your limbs
						covered with golden plumage.
					</p>

					<p>
						But, so that your song, born sweetly in our ears, and
						your rich vocal gift, might not be lost, each virgin face
						and human voice remained.
					</p>

				</section>


				<section class="section">

					<div class="section-header">
						<h2>Researcher's note</h2>
					</div>

					<p>
						This is perhaps the most unusual source in the archive.
						The Sirens are explicitly connected with the search for
						Persephone.
					</p>

					<p>
            The significance of
            <a
              href="https://en.wikipedia.org/wiki/Proserpina"
              target="_blank"
              rel="noreferrer"
            >
              Persephone
            </a>
            is unclear. It may refer
            to a person, a location, or a figure whose original
            meaning has been lost through translation.
          </p>

				</section>


			<!-- =================================================
			     ARTICLES INDEX
			     ================================================= -->

			{:else if currentPage === 'articles'}

				<section class="intro">

					<h2>Research notes</h2>

					<p class="subtitle">
						Articles and notes concerning the material collected
						in this archive.
					</p>

					<p>
						These notes represent the author's own observations
						and should not be confused with the source material
						itself.
					</p>

				</section>


				<section class="section">

					<div class="section-header">

						<h2>Articles</h2>

						<span>2 entries</span>

					</div>


					{#each articles as article}

						<article class="post">

							<h3>

								<a
									href="/"
									on:click|preventDefault={() =>
										navigate(article.id)
									}
								>
									{article.title}
								</a>

							</h3>

							<div class="post-meta">
								Posted {article.date} — {article.category}
							</div>

							<p>

								{#if article.id === 'article-chorus'}

									The three figures described in the oldest
									available fragment may correspond to several
									later traditions concerning Sirens. Their
									relationship to Persephone, however, remains
									unclear.

								{:else}

									The name does not appear to correspond
									directly to the name of a known Sairen ruler.
									It may instead be a translated title or epithet.

								{/if}

							</p>

							<a
								href="/"
								on:click|preventDefault={() =>
									navigate(article.id)
								}
							>
								Continue reading...
							</a>

						</article>

					{/each}

				</section>


			<!-- =================================================
			     ARTICLE — CHORUS
			     ================================================= -->

			{:else if currentPage === 'article-chorus'}

				<section class="intro">

					<h2>The Chorus: A Study of an Obscure Sairen Myth</h2>

					<div class="post-meta">
						Posted 02/06/31 — Research / Mythology
					</div>

					<p class="subtitle">
						An attempt to compare several apparently unrelated
						accounts of three singing figures.
					</p>

				</section>

        <section class="section">

          <h2>I. Introduction</h2>

          <p>
            Among the surviving traditions of Sairen mythology, few figures are as
            difficult to reconstruct as the three entities commonly translated as
            <strong>the Chorus</strong>.
          </p>

          <p>
            The name itself is somewhat problematic. The Sairen word appearing in
            the oldest manuscripts does not have an exact equivalent in Imperial.
            <em>Chorus</em> is perhaps the closest translation, although it carries
            several meanings that may not have been intended by the original
            authors. It can refer to a group of singers, a collective voice, or,
            in some contexts, a group acting as a single entity. This last meaning
            seems particularly important.
          </p>

          <p>
            The Chorus is consistently described as three sisters who sing together,
            yet the surviving texts rarely distinguish between their individual
            actions. Their names are frequently absent, damaged, or deliberately
            obscured in later copies. Even where individual names appear to have
            survived, their forms vary considerably between manuscripts.
          </p>

          <p>
            This has led some Sairen scholars to argue that the Chorus may
            originally have been a single mythological entity divided into three
            aspects. Others consider the three to have always been separate
            individuals. The available evidence does not allow us to settle the
            question.
          </p>

          <p>
            What can be established with considerably more confidence is that the
            three occupy a peculiar position in Sairen mythology. They are not
            simply monsters, nor are they ordinary divine figures. They represent
            a very specific violation of what appears to be one of the fundamental
            principles of traditional Sairen society:
          </p>

          <blockquote>
            <strong>the individual voice must serve the greater song.</strong>
          </blockquote>

          <p>
            The Chorus represents the opposite. The individual voice becoming
            powerful enough to silence the song of everyone else.
          </p>

        </section>


        <section class="section">

          <h2>II. The Three Sisters</h2>

          <p>
            The oldest version of the story currently available to me is preserved
            in a text which I will refer to as <strong>The Song of the Chorus</strong>.
            Unfortunately, the manuscript's date is impossible to establish with
            any certainty.
          </p>

          <p>
            The language appears archaic in several places, although this may simply
            be the result of deliberate archaism by a later copyist. More
            importantly, the names of the three sisters have been obscured in every
            copy I have been able to locate.
          </p>

          <p>
            The relevant passage reads:
          </p>

          <blockquote>
            “They were sisters, though no mother is named for them, and no egg is
            said to have hatched them. They were simply there, as the sea is there
            and the sky is there.”
          </blockquote>

          <p>
            This is unusual. Sairen mythology normally places considerable
            importance on ancestry, lineage and the circumstances of birth. The
            statement that the three were simply <em>there</em> may therefore
            indicate that the author considered them primordial beings.
          </p>

          <p>
            It is also possible that this is purely literary language. Nevertheless,
            the same idea appears elsewhere. The Chorus are not said to have been
            born, are not said to have died, are not given parents. They simply
            appear at the beginning of the story.
          </p>

          <p>
            Their names are similarly uncertain. In the copy examined here, all
            three are replaced by blocks of redaction. Whether this was done by
            the original author, by an Imperial censor, or by a much later editor
            is unknown. The text calls them sisters and gives them one collective
            name:
            <strong>the Chorus.</strong>
          </p>

        </section>


        <section class="section">

          <h2>III. The Song</h2>

          <p>
            The abilities attributed to the three are remarkably consistent across
            the surviving traditions. They possess voices of exceptional beauty and
            range. Their songs can travel farther than ordinary Sairen songs.
            Those who hear them are said to become unable to think about anything
            else. The Chorus can calm fear, excite happiness, and disturb
            concentration.
          </p>

          <p>
            These descriptions are interesting because they do not necessarily
            require supernatural explanations. Modern Sairen biology already
            provides a possible basis for some of these claims. Sairen vocalisation
            is extraordinarily complex, and their known neuroacoustic abilities
            can affect the emotional and attentional states of other species.
          </p>

          <p>
            It is therefore tempting to assume that the original story exaggerated
            a real biological phenomenon. However, this interpretation becomes
            less satisfactory later in the text. The Chorus are not merely
            described as influencing their listeners. They are described as
            <strong>directing them</strong>.
          </p>

          <p>
            The three sisters supposedly travelled from settlement to settlement,
            attracting Sairens to themselves. Some followed willingly. Others were
            unable to leave. Some eventually forgot why they had opposed the
            Chorus in the first place.
          </p>

          <p>
            The text then gives what may be the central moral of the entire myth:
          </p>

          <blockquote>
            “A voice exists to join the song, not to silence it.”
          </blockquote>

          <p>
            This sentence may explain why the story survived for so long. The
            Chorus is not condemned because singing is evil. They are condemned
            because they use something that belongs to everyone, the voice, to
            place themselves above everyone else.
          </p>

        </section>


        <section class="section">

          <h2>IV. The Promise of Freedom</h2>

          <p>
            The most interesting contradiction in the story is that the Chorus
            apparently did not initially present themselves as tyrants, they
            promised freedom.
          </p>

          <p>
            According to <em>The Song of the Chorus</em>, their teaching was that
            no Sairen should ever have to obey another. This sounds almost
            paradoxical when compared with their later behaviour. Their supposed
            solution to hierarchy was not equality, however. It was that everyone
            should listen to them.
          </p>

          <p>
            This may be a deliberate criticism of charismatic leaders. The Chorus
            promises to abolish authority while simultaneously making themselves
            the only authority. It is possible that this part of the myth was
            added or altered during a later political period. If so, the Chorus
            may originally have represented something entirely different.
            Unfortunately, there is currently insufficient evidence to determine
            this.
          </p>

        </section>


        <section class="section">

          <h2>V. Orphée</h2>

          <p>
            The second major figure in the tradition is a ruler whose original name
            has been lost. The Sairen text gives only a series of redacted
            characters. The Chorus, however, calls him <strong>Orphée</strong>.
            This is almost certainly not his historical name.
          </p>

          <p>
            The word appears to be a title or epithet, and its exact Sairen meaning
            remains uncertain. The text describes Orphée as a ruler who arrived
            “from beyond the stars.”
          </p>

          <p>
            This phrase has produced considerable disagreement. The most
            conservative interpretation is that it simply means a foreign ruler,
            possibly one arriving from another territory. A more literal
            interpretation would imply extraterrestrial origin.
          </p>

          <p>
            According to the Chorus tradition, Orphée does not defeat the three
            sisters through military force, he answers their song. His followers
            then became known as <strong>the Muses</strong>. However, it might only
            be a poetic interpretation.
          </p>

        </section>


        <section class="section">

          <h2>VI. The Muses</h2>

          <p>
            The term <em>Muses</em> presents another problem. It clearly has a
            negative meaning within the Chorus tradition.
          </p>

          <p>
            The Muses are described as Sairens who have abandoned their own voices
            and now sing only what they have been taught. This appears to be a
            political insult rather than a description of a specific ethnic or
            religious group.
          </p>

          <p>
            The Muses represent obedience. The Chorus represents individual
            freedom. Yet, once again, the story refuses to make this opposition
            simple. The Muses sing of duty and unity. This is the point where the
            Chorus loses.
          </p>

          <p>
            One could interpret this as a straightforward moral lesson: individual
            freedom becomes dangerous when it threatens communal survival. This
            interpretation would fit extremely well with later Sairen political
            philosophy.
          </p>

          <p>
            But there may be another explanation. If Orphée was in fact an early
            Imperial ruler, the story may preserve a distorted memory of a real
            political conflict. In that case, the Chorus may have been historical
            dissidents who opposed Imperial rule, while the “Muses” were simply
            supporters of the new order.
          </p>

          <p>
            The language of the surviving myth would then have been shaped by
            whoever preserved it. Unfortunately, this is impossible to prove.
          </p>

        </section>


        <section class="section">

          <h2>VII. The Contest of Voices</h2>

          <p>
            The actual contest between the Chorus and the Muses is surprisingly
            brief. The three sisters each sing. The Muses answer by singing of
            duty, unity and the Sairen people. The audience chooses the Muses.
            The Chorus simply loses.
          </p>

          <p>
            This may be the oldest surviving example of a recurring idea in Sairen
            literature: that the greatest threat to a community is not necessarily
            a stronger enemy, but a voice capable of persuading its members to
            abandon the collective.
          </p>

          <p>
            The conclusion is therefore almost ideological. The Muses do not prove
            that their song is more beautiful but that it is the song the community
            chooses.
          </p>

        </section>


        <section class="section">

          <h2>VIII. The Plucking of the Feathers</h2>

          <p>
            The punishment that follows is considerably stranger. The Muses strip
            the three sisters of their feathers and make crowns from them.
          </p>

          <p>
            This detail appears in another tradition concerning the Chorus,
            although the surrounding story is considerably different. In this
            second tradition, the three are said to have challenged the Muses to
            a contest of singing and lost. Their feathers were then removed and
            made into crowns.
          </p>

          <p>
            It is impossible to determine whether these are two accounts of the
            same event or two independent traditions which eventually became
            confused with one another.
          </p>

          <p>
            The feather appears to have considerable symbolic importance in Sairen
            culture. To remove the feathers of another Sairen is therefore unlikely
            to have been understood merely as physical punishment. It may represent
            humiliation, loss of identity, or the destruction of one's ability to
            participate in communal activities. Alternatively, it may preserve a
            memory of an actual mutilation.
          </p>

          <p>
            I would not normally consider such an interpretation without
            archaeological evidence. Unfortunately, there is some evidence that
            the earliest versions of the Chorus tradition may have originated
            during a period in which mutilation of defeated enemies was not
            unknown.
          </p>

          <p>
            This remains speculative.
          </p>

        </section>


        <section class="section">

          <h2>IX. The Search for Persephone</h2>

          <p>
            The strangest element of the mythology appears in a separate group of
            texts. These texts associate the Chorus with a figure or place called
            <strong>Persephone</strong>.
          </p>

          <p>
            The oldest surviving version is extremely fragmentary. It states that
            the three were once companions of Persephone, and that after Persephone
            disappeared they searched for her across the world. In some versions,
            the three requested wings so that they could cross the sea in their
            search.
          </p>

          <p>
            This would explain an otherwise peculiar feature of the mythology:
            why the Chorus possesses both humanoid and bird-like characteristics
            in some descriptions.
          </p>

          <p>
            The interpretation of Persephone is much more difficult. No Sairen
            source I have examined clearly identifies Persephone.
          </p>

          <p>
            She is sometimes described as a person. Elsewhere, the wording suggests
            a place. In the Chorus tradition, one of the sister's final prophecy
            states:
          </p>

          <blockquote>
            “When we return, we will find Persephone.”
          </blockquote>

          <p>
            The phrase is sufficiently obscure that I am reluctant to translate it
            more freely. The verb <em>return</em> is particularly interesting.
            Return from where? And to where?
          </p>

          <p>
            If Persephone was a person, the statement could mean that the Chorus
            intended to find her after their imprisonment. If Persephone was a
            place, it could indicate that the three believed themselves exiles.
            There is also the possibility that <em>Persephone</em> is not a proper
            name at all, but an ancient Sairen word which has been preserved through
            translation.
          </p>

          <p>
            This possibility deserves further study.
          </p>

        </section>


        <section class="section">

          <h2>X. Orphée and the Sirens</h2>

          <p>
            A separate tradition provides an unexpected parallel. In the surviving
            Sairen translation, Orphée encounters the three singers during a voyage.
            Their song nearly causes the travellers to abandon their journey, but
            Orphée answers them with music of his own.
          </p>

          <p>
            His music overcomes theirs. The vessel continues its journey. This
            account differs from <em>The Song of the Chorus</em> in several
            important ways.
          </p>

          <p>
            There is no mention of the Muses, no political rebellion and no
            punishment. The three are simply dangerous singers encountered during
            a voyage. This suggests that the Orphée tradition may predate the
            political interpretation of the Chorus.
          </p>

          <p>
            It may even be the oldest layer of the myth. If so, the later Sairen
            tradition may have taken an older story about three supernatural
            singers and transformed them into political enemies of the community.
            This would not be unusual in mythology.
          </p>

          <p>
            Historical enemies are frequently transformed into monsters, while
            monsters are sometimes created from memories of historical enemies.
          </p>

        </section>


        <section class="section">

          <h2>XI. What Were the Chorus?</h2>

          <p>
            After comparing the surviving material, I believe there are three
            principal possibilities.
          </p>

          <h3>1. The Chorus were entirely mythical.</h3>

          <p>
            Under this interpretation, the three are symbolic figures representing
            dangerous individualism, manipulation and the rejection of communal
            responsibility. This would explain the moral consistency of the modern
            tradition.
          </p>

          <h3>2. The Chorus were historical Sairens later mythologised.</h3>

          <p>
            Under this interpretation, the three were real individuals who opposed
            an early Imperial regime. Their abilities may have been exaggerated
            over time until they became supernatural.
          </p>

          <h3>3. The Chorus were real individuals whose history was deliberately
            mythologised.</h3>

          <p>
            This possibility is, in my opinion, the most difficult and therefore
            the most interesting. Perhaps there really were three Sairens who
            possessed unusual neuroacoustic abilities. Perhaps they really did
            oppose the early Imperium. Perhaps they really were imprisoned. And
            perhaps later Imperial writers transformed their rebellion into the
            story we now possess.
          </p>

          <p>
            If this is true, then the surviving mythology is not a historical
            account. It is propaganda. But it is propaganda containing fragments
            of history.
          </p>

        </section>


        <section class="section">

          <h2>XII. The Question of Immortality</h2>

          <p>
            There is one final problem which I have deliberately avoided until
            this point. The Chorus is never explicitly said to die.
          </p>

          <p>
            In fact, several passages appear to imply the opposite. The three are
            imprisoned, silenced and forgotten. But nowhere are they killed. Their
            final prophecy is also phrased in the future tense.
          </p>

          <blockquote>
            <strong>“The Chorus will sing again.”</strong>
          </blockquote>

          <p>
            This could, of course, simply be a conventional mythological threat.
            However, if the original stories were based upon historical figures,
            this wording becomes much harder to explain.
          </p>

          <p>
            Why would later authors preserve a belief that three defeated rebels
            would return?
          </p>

          <p>
            One possible explanation is that the Chorus became a metaphor for
            political rebellion itself. Another is that the original authors
            genuinely believed the three were immortal. I have found no reliable
            evidence that they were, nor have I found evidence that they were not.
          </p>

        </section>


        <section class="section warning">

          <h2>Conclusion</h2>

          <p>
            The Chorus occupies an unusual place in Sairen mythology. They are
            simultaneously singers, monsters, rebels, sisters, political enemies
            and possibly something older.
          </p>

          <p>
            The surviving traditions disagree about almost everything except the
            essential elements.
          </p>

          <p>
            There were three. They sang. Their songs were dangerous. They opposed
            Orphée. The Muses defeated them. They were deprived of their feathers.
            And they were imprisoned.
          </p>

          <p>
            Beyond this, certainty becomes difficult. Their names are missing from
            some of the oldest texts. Their origin is unknown. Their relationship
            with Persephone is unclear. Their supposed immortality cannot be
            confirmed. Even the identity of Orphée remains uncertain.
          </p>

          <p>
            For this reason, I believe the Chorus should not be dismissed as a
            simple morality tale. There may be a historical event buried beneath
            the mythology. Perhaps even several.
          </p>

          <p>
            The most intriguing possibility is that the oldest texts preserve not
            the story of three mythical monsters, but the distorted memory of
            three real Sairens who lived during the transition into the Imperial
            period. If that is true, then their final prophecy may deserve more
            attention than it has received.
          </p>

          <blockquote>
            “When we return, we will find Persephone.”
          </blockquote>

          <p>
            I have no idea what Persephone was. I suspect, however, that the answer
            to that question may tell us considerably more about the Chorus than
            the stories about their songs ever could.
          </p>

        </section>


				<section class="section">

					<a
						href="/"
						on:click|preventDefault={() => navigate('articles')}
					>
						&lt;&lt; Return to research notes
					</a>

				</section>


			<!-- =================================================
			     ARTICLE — ORPHÉE
			     ================================================= -->

			{:else if currentPage === 'article-orphee'}

				<section class="intro">

					<h2>Notes on the name "Orphée"</h2>

					<div class="post-meta">
						Posted 17/16/30 — Sources / Linguistics
					</div>

					<p class="subtitle">
						Preliminary observations concerning the figure who
						appears to oppose the Chorus through song.
					</p>

				</section>


				<section class="section">

					<h2>The name</h2>

					<p>
						The name Orphée does not appear to correspond directly
						to the name of a known Sairen ruler.
					</p>

					<p>
						It may therefore represent a translated name, title,
						or epithet rather than a personal name.
					</p>

				</section>


				<section class="section">

					<h2>Music against music</h2>

					<p>
						The most interesting feature of the tradition is that
						Orphée does not defeat the Sirens through physical force.
					</p>

					<p>
						Instead, he answers their song with another song.
					</p>

					<p>
						This detail appears significant when compared with
						the account of the Chorus and the Muses.
					</p>

				</section>


				<section class="section warning">

					<h2>Unresolved question</h2>

					<p>
						It is currently impossible to determine whether the
						name Orphée represents an actual historical individual,
						a title, or a later literary construction.
					</p>

				</section>


				<section class="section">

					<a
						href="/"
						on:click|preventDefault={() => navigate('articles')}
					>
						&lt;&lt; Return to research notes
					</a>

				</section>


			<!-- =================================================
			     ABOUT
			     ================================================= -->

			{:else if currentPage === 'about'}

				<section class="intro">

					<h2>About this archive</h2>

					<p class="subtitle">
						An independent research project concerning Sairen mythology.
					</p>

					<p>
						Sairen Studies was established in 29AGS as a personal
						archive for material concerning Sairen mythology and
						its relationship to older maritime traditions.
					</p>

					<p>
						The archive began as a collection of references and
						translated passages. It has since expanded to include
						comparative notes, annotations and material which does
						not appear to have been properly classified elsewhere.
					</p>

				</section>


				<section class="section">

					<div class="section-header">
						<h2>About the author</h2>
					</div>

					<p>
						The author is an independent researcher with an interest
						in ancient mythology, comparative religion and historical
						linguistics.
					</p>

					<p>
						This website is not affiliated with any university,
						museum, government institution or archaeological
						organisation.
					</p>

				</section>


				<section class="section">

					<div class="section-header">
						<h2>Archive policy</h2>
					</div>

					<p>
						Translations are identified as such whenever possible.
						Interpretations and personal hypotheses are kept separate
						from the source texts.
					</p>

					<p>
						Material of uncertain origin is retained when it appears
						relevant, but is marked accordingly.
					</p>

				</section>


				<section class="section warning">

					<h2>Disclaimer</h2>

					<p>
						The information contained in this archive has not been
						independently verified in every case.
					</p>

					<p>
						Readers are encouraged to consult the original
						publications before using any material for academic
						purposes.
					</p>

				</section>



      {:else if currentPage === 'restricted'}

        <section class="intro">

          <h2>Restricted archive</h2>

          <p class="subtitle">
            Access granted.
          </p>

          <p>
            This section of the archive is currently being prepared.
          </p>

          <p>
            Additional material will be made available here at a later date.
          </p>

        </section>


        <section class="section warning">

          <h2>Archive status</h2>

          <p>
            This document has not yet been published.
          </p>

          <p>
            Please return later.
          </p>

        </section>


        <section class="section">

          <a
            href="/"
            on:click|preventDefault={() => navigate('home')}
          >
            &lt;&lt; Return to the archive
          </a>

        </section>


			<!-- =================================================
			     FALLBACK
			     ================================================= -->

			{:else}

				<section class="intro">

					<h2>Page not found</h2>

					<p class="subtitle">
						The requested archive entry does not exist.
					</p>

					<p>
						<a
							href="/"
							on:click|preventDefault={() => navigate('home')}
						>
							&lt;&lt; Return to the archive
						</a>
					</p>

				</section>

			{/if}

		</main>

	</div>


	<!-- =====================================================
	     FOOTER
	     ===================================================== -->

	<footer class="footer">

    <p>
      <a
        href="/"
        on:click|preventDefault={() => navigate('about')}
      >
        About
      </a>
      ·
      <a
        href="/"
        on:click|preventDefault={() => navigate('articles')}
      >
        Articles
      </a>
      ·
      <a
        href="/"
        on:click|preventDefault={() => navigate('sources')}
      >
        Sources
      </a>
      ·
      <a
        href="https://youtu.be/N7QSavYWEE0"
        target="_blank"
        rel="noreferrer"
      >
        Contact
      </a>
    </p>

	</footer>

</div>