# **ERRORS AND HOW TO RESOLVE THEM**

Errors in Substrate-based chains are usually accompanied by descriptive messages. The substrate explorer translates and displays those descriptive messages to help users understand what might have caused the error or inform the user about performed on-chain actions.

If this page does not answer your question, try to reach out to the community and us on [Discord](https://discord.gg/NeExTVSs) for more information on troubleshooting your issue.

---

## **How to get detailed error descriptions**

Here's how to find out the detailed error description with the help of the substrate explorer.

A typical failed transactions looks something like this:

![img](assets/failed-tx-error-msg.jpg#center)

The image displays only the error name as defined in the code, not its error message. Despite this error being rather self-explanatory, let's find its details.

In the [explorer tab](https://substrate-explorer-testnet.swapdex.network/?rpc=wss%3A%2F%2Frpc-testnet.swapdex.network%2Fws#/explorer), find the block in which this failure occurred. Then, expand the `system.ExtrinsicFailed` frame:

![img](assets/failed-tx-error-detail.jpg#center)

Notice how the `details` field contains a human-readable description of the error. Most errors will have this, if looked up this way.
If you cannot look up the error this way, or there is no message in the details field, consult the table below.

---

## **Common Errors**

The table below lists the most commonly encountered errors and ways to resolve them.

<style>


:root {
    --bg-table-stripe: #f6f6f5;
    --b-table: #e3e3e2;
    --caption: #EC4880;
}

table {
    background-color: transparent;
    border-collapse:collapse;
  	font-family: Arial, Helvetica, sans-serif
}

th {
    text-align:left
}

.dcf-txt-center {
      text-align: center!important
    }

    .dcf-txt-left {
      text-align: left!important
    }

    .dcf-txt-right {
      text-align: right!important
    }
    
.dcf-table caption {
      color: var(--caption);
      font-size: 1.13em;
      font-weight: 700;
      padding-bottom: .56rem
    }

    .dcf-table thead {
      font-size: .84em
    }

    .dcf-table tbody {
      border-bottom: 1px solid var(--b-table);
      border-top: 1px solid var(--b-table);
      font-size: .84em
    }

    .dcf-table tfoot {
      font-size: .84em
    }

    .dcf-table td, .dcf-table th {
      padding-right: 1.78em
    }

    .dcf-table-bordered, .dcf-table-bordered td, .dcf-table-bordered th {
      border: 1px solid var(--b-table)
    }

    .dcf-table-bordered td, .dcf-table-bordered th, .dcf-table-striped td, .dcf-table-striped th {
      padding-left: 1em;
      padding-right: 1em
    }

    .dcf-table-bordered tr:not(:last-child), .dcf-table-striped tr:not(:last-child) {
      border-bottom: 1px solid var(--b-table)
    }

    .dcf-table-striped tbody tr:nth-of-type(2n) {
      background-color: var(--bg-table-stripe)
    }

    .dcf-table thead td, .dcf-table thead th {
      padding-bottom: .75em;
      vertical-align: bottom;
	  background-color: #EC4880
    }
	
	th[scope=row] {
    background-color: #D9D8DA;
}

    .dcf-table tbody td, .dcf-table tbody th, .dcf-table tfoot td, .dcf-table tfoot th {
      padding-top: .75em;
      vertical-align: top
    }

    .dcf-table tbody td, .dcf-table tbody th {
      padding-bottom: .75em
    }

    .dcf-table-bordered thead th {
      padding-top: 1.33em
    }

    .dcf-wrapper-table-scroll {
      overflow-x: auto;
      -webkit-overflow-scrolling: touch;
      left: 50%;
      margin-left: -50vw;
      margin-right: -50vw;
      padding-bottom: 1em;
      position: relative;
      right: 50%;
      width: 100vw
    }

    @media only screen and (max-width:42.09em) {
      .dcf-table-responsive thead {
        clip: rect(0 0 0 0);
        -webkit-clip-path: inset(50%);
        clip-path: inset(50%);
        height: 1px;
        overflow: hidden;
        position: absolute;
        width: 1px;
        white-space: nowrap
      }
      .dcf-table-responsive tr {
        display: block
      }
      .dcf-table-responsive td {
        -webkit-column-gap: 3.16vw;
        -moz-column-gap: 3.16vw;
        column-gap: 3.16vw;
        display: grid;
        grid-template-columns: 1fr 2fr;
        text-align: left!important
      }
      .dcf-table-responsive.dcf-table-bordered, .dcf-table-responsive.dcf-table-bordered thead th {
        border-width: 0
      }
      .dcf-table-responsive.dcf-table-bordered tbody td {
        border-top-width: 0
      }
      .dcf-table-responsive:not(.dcf-table-bordered) tbody tr {
        padding-bottom: .75em
      }
      .dcf-table-responsive:not(.dcf-table-bordered) tbody td {
        padding-bottom: 0
      }
      .dcf-table-responsive:not(.dcf-table-bordered):not(.dcf-table-striped) tbody td {
        padding-right: 0
      }
      .dcf-table-responsive.dcf-table-bordered tbody tr:last-child td:last-child {
        border-bottom-width: 0
      }
      .dcf-table-responsive tbody td:before {
        content: attr(data-label);
        float: left;
        font-weight: 700;
        padding-right: 1.78em
      }
    }

.dcf-overflow-x-auto {
      overflow-x: auto!important;
      -webkit-overflow-scrolling: touch
    }
    
</style>

<table class="dcf-table dcf-table-responsive dcf-table-bordered dcf-table-striped dcf-w-100%">
	<thead>
		<tr>
			<th scope="col">Error</th>
			<th scope="col">Description</th>
			<th scope="col">Solution</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<th scope="row">BadOrigin</th>
			<td data-label="Desctiption">You are not allowed to do this operation, e.g. trying to create a council motion with a non-council account.</td>
			<td data-label="Solution">Either switch to an account that has the necessary permissions, or check if the operation you're trying to execute is permitted at all (e.g. calling system.setCode to do a runtime upgrade directly, without voting).</td>
		</tr>
		<tr>
			<th scope="row">BadProof</th>
			<td data-label="Desctiption">The transaction's signature seems invalid.</td>
			<td data-label="Solution">It's possible that the node you're connected to is following an obsolete fork - trying again after it catches up usually resolves the issue. To check for bigger problems, inspect the last finalized and current best block of the node you're connected to and compare the values to chain stats exposed by other nodes - are they in sync? If not, try connecting to a different node.</td>
		</tr>
		<tr>
			<th scope="row">Future</th>
			<td data-label="Desctiption">Transaction nonce too high, i.e. it's &quot;from the future&quot;.</td>
			<td data-label="Solution">Reduce the nonce to +1 of current nonce. Check current nonce by inspecting the address you're using to send the transaction.</td>
		</tr>
		<tr>
			<th scope="row">Stale</th>
			<td data-label="Desctiption">Transaction nonce too low.</td>
			<td data-label="Solution">Increase the nonce to +1 of current nonce. Check current nonce by inspecting the address you're using to send the transaction.</td>
		</tr>
		<tr>
			<th scope="row">ExhaustsResources</th>
			<td data-label="Desctiption">There aren't enough resources left in the current block to submit this transaction.</td>
			<td data-label="Solution">Try again in the next block.</td>
		</tr>
		<tr>
			<th scope="row">Payment</th>
			<td data-label="Desctiption">Unable to pay for TX fee.</td>
			<td data-label="Solution">You might not have enough free balance to cover the fee this transaction would incur.</td>
		</tr>
		<tr>
			<th scope="row">Temporarily banned</th>
			<td data-label="Desctiption">The transaction is temporarily banned.</td>
			<td data-label="Solution">The tx is already in pool. Either try on a different node, or wait to see if the initial transaction goes through.</td>
		</tr>
	</tbody>
</table>

---

## **Error Table**

The below table is a reference to the errors that exists in Kusari and SwapDex. It is generated from the runtime's metadata.

<style>


:root {
    --bg-table-stripe: #f6f6f5;
    --b-table: #e3e3e2;
    --caption: #EC4880;
}

table {
    background-color: transparent;
    border-collapse:collapse;
  	font-family: Arial, Helvetica, sans-serif
}

th {
    text-align:left
}

.dcf-txt-center {
      text-align: center!important
    }

    .dcf-txt-left {
      text-align: left!important
    }

    .dcf-txt-right {
      text-align: right!important
    }
    
.dcf-table caption {
      color: var(--caption);
      font-size: 1.13em;
      font-weight: 700;
      padding-bottom: .56rem
    }

    .dcf-table thead {
      font-size: .84em;
    }

    .dcf-table tbody {
      border-bottom: 1px solid var(--b-table);
      border-top: 1px solid var(--b-table);
      font-size: .84em
    }

    .dcf-table tfoot {
      font-size: .84em
    }

    .dcf-table td, .dcf-table th {
      padding-right: 1.78em
    }

    .dcf-table-bordered, .dcf-table-bordered td, .dcf-table-bordered th {
      border: 1px solid var(--b-table)
    }

    .dcf-table-bordered td, .dcf-table-bordered th, .dcf-table-striped td, .dcf-table-striped th {
      padding-left: 1em;
      padding-right: 1em
    }

    .dcf-table-bordered tr:not(:last-child), .dcf-table-striped tr:not(:last-child) {
      border-bottom: 1px solid var(--b-table)
    }

    .dcf-table-striped tbody tr:nth-of-type(2n) {
      background-color: var(--bg-table-stripe)
    }

    .dcf-table thead td, .dcf-table thead th {
      padding-bottom: .75em;
      vertical-align: bottom;
	  background-color: #EC4880
    }
	
	th[scope=row] {
    background-color: #D9D8DA;
}

    .dcf-table tbody td, .dcf-table tbody th, .dcf-table tfoot td, .dcf-table tfoot th {
      padding-top: .75em;
      vertical-align: top
    }

    .dcf-table tbody td, .dcf-table tbody th {
      padding-bottom: .75em
    }

    .dcf-table-bordered thead th {
      padding-top: 1.33em
    }

    .dcf-wrapper-table-scroll {
      overflow-x: auto;
      -webkit-overflow-scrolling: touch;
      left: 50%;
      margin-left: -50vw;
      margin-right: -50vw;
      padding-bottom: 1em;
      position: relative;
      right: 50%;
      width: 100vw
    }

    @media only screen and (max-width:42.09em) {
      .dcf-table-responsive thead {
        clip: rect(0 0 0 0);
        -webkit-clip-path: inset(50%);
        clip-path: inset(50%);
        height: 1px;
        overflow: hidden;
        position: absolute;
        width: 1px;
        white-space: nowrap
      }
      .dcf-table-responsive tr {
        display: block
      }
      .dcf-table-responsive td {
        -webkit-column-gap: 3.16vw;
        -moz-column-gap: 3.16vw;
        column-gap: 3.16vw;
        display: grid;
        grid-template-columns: 1fr 2fr;
        text-align: left!important
      }
      .dcf-table-responsive.dcf-table-bordered, .dcf-table-responsive.dcf-table-bordered thead th {
        border-width: 0
      }
      .dcf-table-responsive.dcf-table-bordered tbody td {
        border-top-width: 0
      }
      .dcf-table-responsive:not(.dcf-table-bordered) tbody tr {
        padding-bottom: .75em
      }
      .dcf-table-responsive:not(.dcf-table-bordered) tbody td {
        padding-bottom: 0
      }
      .dcf-table-responsive:not(.dcf-table-bordered):not(.dcf-table-striped) tbody td {
        padding-right: 0
      }
      .dcf-table-responsive.dcf-table-bordered tbody tr:last-child td:last-child {
        border-bottom-width: 0
      }
      .dcf-table-responsive tbody td:before {
        content: attr(data-label);
        float: left;
        font-weight: 700;
        padding-right: 1.78em
      }
    }

.dcf-overflow-x-auto {
      overflow-x: auto!important;
      -webkit-overflow-scrolling: touch
    }
    
</style>

<table class="dcf-table dcf-table-responsive dcf-table-bordered dcf-table-striped dcf-w-100%">
	<thead>
		<tr>
			<th scope="col">Pallet</th>
			<th scope="col">Error</th>
			<th scope="col">Documentation</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<th scope="row">System (0)</th>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">InvalidSpecName (0)</td>
			<td data-label="Documentation">The name of specification does not match between the current runtime and the new runtime.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">SpecVersionNeedsToIncrease (1)</td>
			<td data-label="Documentation">The specification version is not allowed to decrease between the current runtime and the new runtime.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">FailedToExtractRuntimeVersion (2)</td>
			<td data-label="Documentation">Failed to extract the runtime version from the new runtime. Either calling Core_version or decoding RuntimeVersion failed.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">NonDefaultComposite (3)</td>
			<td data-label="Documentation">Suicide called when the account has non-default composite data.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">NonZeroRefCount (4)</td>
			<td data-label="Documentation">There is a non-zero reference count preventing the account from being purged.</td>
		</tr>
		<tr>
			<th scope="row">Scheduler (1)</th>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">FailedToSchedule (0)</td>
			<td data-label="Documentation">Failed to schedule a call</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">NotFound (1)</td>
			<td data-label="Documentation">Cannot find the scheduled call.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">TargetBlockNumberInPast (2)</td>
			<td data-label="Documentation">Given target block number is in the past.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">RescheduleNoChange (3)</td>
			<td data-label="Documentation">Reschedule failed because it does not change scheduled time.</td>
		</tr>
		<tr>
			<th scope="row">Balances (5)</th>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">VestingBalance (0)</td>
			<td data-label="Documentation">Vesting balance too high to send value</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">LiquidityRestrictions (1)</td>
			<td data-label="Documentation">Account liquidity restrictions prevent withdrawal</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">Overflow (2)</td>
			<td data-label="Documentation">Got an overflow after adding</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">InsufficientBalance (3)</td>
			<td data-label="Documentation">Balance too low to send value</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">ExistentialDeposit (4)</td>
			<td data-label="Documentation">Value too low to create account due to existential deposit</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">KeepAlive (5)</td>
			<td data-label="Documentation">Transfer/payment would kill account</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">ExistingVestingSchedule (6)</td>
			<td data-label="Documentation">A vesting schedule already exists for this account</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">DeadAccount (7)</td>
			<td data-label="Documentation">Beneficiary account must pre-exist</td>
		</tr>
		<tr>
			<th scope="row">Authorship (6)</th>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">InvalidUncleParent (0)</td>
			<td data-label="Documentation">The uncle parent not in the chain.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">UnclesAlreadySet (1)</td>
			<td data-label="Documentation">Uncles already set in the block.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">TooManyUncles (2)</td>
			<td data-label="Documentation">Too many uncles.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">GenesisUncle (3)</td>
			<td data-label="Documentation">The uncle is genesis.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">TooHighUncle (4)</td>
			<td data-label="Documentation">The uncle is too high in chain.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">UncleAlreadyIncluded (5)</td>
			<td data-label="Documentation">The uncle is already included.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">OldUncle (6)</td>
			<td data-label="Documentation">The uncle isn't recent enough to be included.</td>
		</tr>
		<tr>
			<th scope="row">Staking (7)</th>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">NotController (0)</td>
			<td data-label="Documentation">Not a controller account.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">NotStash (1)</td>
			<td data-label="Documentation">Not a stash account.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">AlreadyBonded (2)</td>
			<td data-label="Documentation">Stash is already bonded.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">AlreadyPaired (3)</td>
			<td data-label="Documentation">Controller is already paired.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">EmptyTargets (4)</td>
			<td data-label="Documentation">Targets cannot be empty.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">DuplicateIndex (5)</td>
			<td data-label="Documentation">Duplicate index.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">InvalidSlashIndex (6)</td>
			<td data-label="Documentation">Slash record index out of bounds.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">InsufficientValue (7)</td>
			<td data-label="Documentation">Can not bond with value less than minimum balance.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">NoMoreChunks (8)</td>
			<td data-label="Documentation">Can not schedule more unlock chunks.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">NoUnlockChunk (9)</td>
			<td data-label="Documentation">Can not rebond without unlocking chunks.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">FundedTarget (10)</td>
			<td data-label="Documentation">Attempting to target a stash that still has funds.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">InvalidEraToReward (11)</td>
			<td data-label="Documentation">Invalid era to reward.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">InvalidNumberOfNominations (12)</td>
			<td data-label="Documentation">Invalid number of nominations.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">NotSortedAndUnique (13)</td>
			<td data-label="Documentation">Items are not sorted and unique.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">AlreadyClaimed (14)</td>
			<td data-label="Documentation">Rewards for this era have already been claimed for this validator.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">OffchainElectionEarlySubmission (15)</td>
			<td data-label="Documentation">The submitted result is received out of the open window.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">OffchainElectionWeakSubmission (16)</td>
			<td data-label="Documentation">The submitted result is not as good as the one stored on chain.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">SnapshotUnavailable (17)</td>
			<td data-label="Documentation">The snapshot data of the current window is missing.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">OffchainElectionBogusWinnerCount (18)</td>
			<td data-label="Documentation">Incorrect number of winners were presented.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">OffchainElectionBogusWinner (19)</td>
			<td data-label="Documentation">One of the submitted winners is not an active candidate on chain (index is out of range in snapshot).</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">OffchainElectionBogusCompact (20)</td>
			<td data-label="Documentation">Error while building the assignment type from the compact. This can happen if an index is invalid, or if the weights overflow.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">OffchainElectionBogusNominator (21)</td>
			<td data-label="Documentation">One of the submitted nominators is not an active nominator on chain.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">OffchainElectionBogusNomination (22)</td>
			<td data-label="Documentation">One of the submitted nominators has an edge to which they have not voted on chain.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">OffchainElectionSlashedNomination (23)</td>
			<td data-label="Documentation">One of the submitted nominators has an edge which is submitted before the last non-zero slash of the target.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">OffchainElectionBogusSelfVote (24)</td>
			<td data-label="Documentation">A self vote must only be originated from a validator to ONLY themselves.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">OffchainElectionBogusEdge (25)</td>
			<td data-label="Documentation">The submitted result has unknown edges that are not among the presented winners.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">OffchainElectionBogusScore (26)</td>
			<td data-label="Documentation">The claimed score does not match with the one computed from the data.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">OffchainElectionBogusElectionSize (27)</td>
			<td data-label="Documentation">The election size is invalid.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">CallNotAllowed (28)</td>
			<td data-label="Documentation">The call is not allowed at the given time due to restrictions of election period.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">IncorrectHistoryDepth (29)</td>
			<td data-label="Documentation">Incorrect previous history depth input provided.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">IncorrectSlashingSpans (30)</td>
			<td data-label="Documentation">Incorrect number of slashing spans provided.</td>
		</tr>
		<tr>
			<th scope="row">Session (9)</th>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">InvalidProof (0)</td>
			<td data-label="Documentation">Invalid ownership proof.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">NoAssociatedValidatorId (1)</td>
			<td data-label="Documentation">No associated validator ID for account.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">DuplicatedKey (2)</td>
			<td data-label="Documentation">Registered duplicate key.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">NoKeys (3)</td>
			<td data-label="Documentation">No keys are associated with this account.</td>
		</tr>
		<tr>
			<th scope="row">Grandpa (11)</th>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">PauseFailed (0)</td>
			<td data-label="Documentation">Attempt to signal GRANDPA pause when the authority set isn't live (either paused or already pending pause).</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">ResumeFailed (1)</td>
			<td data-label="Documentation">Attempt to signal GRANDPA resume when the authority set isn't paused (either live or already pending resume).</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">ChangePending (2)</td>
			<td data-label="Documentation">Attempt to signal GRANDPA change with one already pending.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">TooSoon (3)</td>
			<td data-label="Documentation">Cannot signal forced change so soon after last.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">InvalidKeyOwnershipProof (4)</td>
			<td data-label="Documentation">A key ownership proof provided as part of an equivocation report is invalid.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">InvalidEquivocationProof (5)</td>
			<td data-label="Documentation">An equivocation proof provided as part of an equivocation report is invalid.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">DuplicateOffenceReport (6)</td>
			<td data-label="Documentation">A given equivocation report is valid but already previously reported.</td>
		</tr>
		<tr>
			<th scope="row">ImOnline (12)</th>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">InvalidKey (0)</td>
			<td data-label="Documentation">Non existent public key.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">DuplicatedHeartbeat (1)</td>
			<td data-label="Documentation">Duplicated heartbeat.</td>
		</tr>
		<tr>
			<th scope="row">Democracy (14)</th>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">ValueLow (0)</td>
			<td data-label="Documentation">Value too low</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">ProposalMissing (1)</td>
			<td data-label="Documentation">Proposal does not exist</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">BadIndex (2)</td>
			<td data-label="Documentation">Unknown index</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">AlreadyCanceled (3)</td>
			<td data-label="Documentation">Cannot cancel the same proposal twice</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">DuplicateProposal (4)</td>
			<td data-label="Documentation">Proposal already made</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">ProposalBlacklisted (5)</td>
			<td data-label="Documentation">Proposal still blacklisted</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">NotSimpleMajority (6)</td>
			<td data-label="Documentation">Next external proposal not simple majority</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">InvalidHash (7)</td>
			<td data-label="Documentation">Invalid hash</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">NoProposal (8)</td>
			<td data-label="Documentation">No external proposal</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">AlreadyVetoed (9)</td>
			<td data-label="Documentation">Identity may not veto a proposal twice</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">NotDelegated (10)</td>
			<td data-label="Documentation">Not delegated</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">DuplicatePreimage (11)</td>
			<td data-label="Documentation">Preimage already noted</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">NotImminent (12)</td>
			<td data-label="Documentation">Not imminent</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">TooEarly (13)</td>
			<td data-label="Documentation">Too early</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">Imminent (14)</td>
			<td data-label="Documentation">Imminent</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">PreimageMissing (15)</td>
			<td data-label="Documentation">Preimage not found</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">ReferendumInvalid (16)</td>
			<td data-label="Documentation">Vote given for invalid referendum</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">PreimageInvalid (17)</td>
			<td data-label="Documentation">Invalid preimage</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">NoneWaiting (18)</td>
			<td data-label="Documentation">No proposals waiting</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">NotLocked (19)</td>
			<td data-label="Documentation">The target account does not have a lock.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">NotExpired (20)</td>
			<td data-label="Documentation">The lock on the account to be unlocked has not yet expired.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">NotVoter (21)</td>
			<td data-label="Documentation">The given account did not vote on the referendum.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">NoPermission (22)</td>
			<td data-label="Documentation">The actor has no permission to conduct the action.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">AlreadyDelegating (23)</td>
			<td data-label="Documentation">The account is already delegating.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">Overflow (24)</td>
			<td data-label="Documentation">An unexpected integer overflow occurred.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">Underflow (25)</td>
			<td data-label="Documentation">An unexpected integer underflow occurred.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">InsufficientFunds (26)</td>
			<td data-label="Documentation">Too high a balance was provided that the account cannot afford.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">NotDelegating (27)</td>
			<td data-label="Documentation">The account is not currently delegating.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">VotesExist (28)</td>
			<td data-label="Documentation">The account currently has votes attached to it and the operation cannot succeed until these are removed, either through unvote or reap_vote.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">InstantNotAllowed (29)</td>
			<td data-label="Documentation">The instant referendum origin is currently disallowed.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">Nonsense (30)</td>
			<td data-label="Documentation">Delegation to oneself makes no sense.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">WrongUpperBound (31)</td>
			<td data-label="Documentation">Invalid upper bound.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">MaxVotesReached (32)</td>
			<td data-label="Documentation">Maximum number of votes reached.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">InvalidWitness (33)</td>
			<td data-label="Documentation">The provided witness data is wrong.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">TooManyProposals (34)</td>
			<td data-label="Documentation">Maximum number of proposals reached.</td>
		</tr>
		<tr>
			<th scope="row">Council (15)</th>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">NotMember (0)</td>
			<td data-label="Documentation">Account is not a member</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">DuplicateProposal (1)</td>
			<td data-label="Documentation">Duplicate proposals not allowed</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">ProposalMissing (2)</td>
			<td data-label="Documentation">Proposal must exist</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">WrongIndex (3)</td>
			<td data-label="Documentation">Mismatched index</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">DuplicateVote (4)</td>
			<td data-label="Documentation">Duplicate vote ignored</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">AlreadyInitialized (5)</td>
			<td data-label="Documentation">Members are already initialized!</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">TooEarly (6)</td>
			<td data-label="Documentation">The close call was made too early, before the end of the voting.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">TooManyProposals (7)</td>
			<td data-label="Documentation">There can only be a maximum of MaxProposals active proposals.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">WrongProposalWeight (8)</td>
			<td data-label="Documentation">The given weight bound for the proposal was too low.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">WrongProposalLength (9)</td>
			<td data-label="Documentation">The given length bound for the proposal was too low.</td>
		</tr>
		<tr>
			<th scope="row">TechnicalCommittee (16)</th>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">NotMember (0)</td>
			<td data-label="Documentation">Account is not a member</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">DuplicateProposal (1)</td>
			<td data-label="Documentation">Duplicate proposals not allowed</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">ProposalMissing (2)</td>
			<td data-label="Documentation">Proposal must exist</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">WrongIndex (3)</td>
			<td data-label="Documentation">Mismatched index</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">DuplicateVote (4)</td>
			<td data-label="Documentation">Duplicate vote ignored</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">AlreadyInitialized (5)</td>
			<td data-label="Documentation">Members are already initialized!</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">TooEarly (6)</td>
			<td data-label="Documentation">The close call was made too early, before the end of the voting.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">TooManyProposals (7)</td>
			<td data-label="Documentation">There can only be a maximum of MaxProposals active proposals.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">WrongProposalWeight (8)</td>
			<td data-label="Documentation">The given weight bound for the proposal was too low.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">WrongProposalLength (9)</td>
			<td data-label="Documentation">The given length bound for the proposal was too low.</td>
		</tr>
		<tr>
			<th scope="row">ElectionsPhragmen (17)</th>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">UnableToVote (0)</td>
			<td data-label="Documentation">Cannot vote when no candidates or members exist.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">NoVotes (1)</td>
			<td data-label="Documentation">Must vote for at least one candidate.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">TooManyVotes (2)</td>
			<td data-label="Documentation">Cannot vote more than candidates.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">MaximumVotesExceeded (3)</td>
			<td data-label="Documentation">Cannot vote more than maximum allowed.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">LowBalance (4)</td>
			<td data-label="Documentation">Cannot vote with stake less than minimum balance.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">UnableToPayBond (5)</td>
			<td data-label="Documentation">Voter can not pay voting bond.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">MustBeVoter (6)</td>
			<td data-label="Documentation">Must be a voter.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">ReportSelf (7)</td>
			<td data-label="Documentation">Cannot report self.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">DuplicatedCandidate (8)</td>
			<td data-label="Documentation">Duplicated candidate submission.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">MemberSubmit (9)</td>
			<td data-label="Documentation">Member cannot re-submit candidacy.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">RunnerSubmit (10)</td>
			<td data-label="Documentation">Runner cannot re-submit candidacy.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">InsufficientCandidateFunds (11)</td>
			<td data-label="Documentation">Candidate does not have enough funds.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">NotMember (12)</td>
			<td data-label="Documentation">Not a member.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">InvalidCandidateCount (13)</td>
			<td data-label="Documentation">The provided count of number of candidates is incorrect.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">InvalidVoteCount (14)</td>
			<td data-label="Documentation">The provided count of number of votes is incorrect.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">InvalidRenouncing (15)</td>
			<td data-label="Documentation">The renouncing origin presented a wrong Renouncing parameter.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">InvalidReplacement (16)</td>
			<td data-label="Documentation">Prediction regarding replacement after member removal is wrong.</td>
		</tr>
		<tr>
			<th scope="row">Treasury (19)</th>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">InsufficientProposersBalance (0)</td>
			<td data-label="Documentation">Proposer's balance is too low.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">InvalidIndex (1)</td>
			<td data-label="Documentation">No proposal or bounty at that index.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">ReasonTooBig (2)</td>
			<td data-label="Documentation">The reason given is just too big.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">AlreadyKnown (3)</td>
			<td data-label="Documentation">The tip was already found/started.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">UnknownTip (4)</td>
			<td data-label="Documentation">The tip hash is unknown.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">NotFinder (5)</td>
			<td data-label="Documentation">The account attempting to retract the tip is not the finder of the tip.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">StillOpen (6)</td>
			<td data-label="Documentation">The tip cannot be claimed/closed because there are not enough tippers yet.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">Premature (7)</td>
			<td data-label="Documentation">The tip cannot be claimed/closed because it's still in the countdown period.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">UnexpectedStatus (8)</td>
			<td data-label="Documentation">The bounty status is unexpected.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">RequireCurator (9)</td>
			<td data-label="Documentation">Require bounty curator.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">InvalidValue (10)</td>
			<td data-label="Documentation">Invalid bounty value.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">InvalidFee (11)</td>
			<td data-label="Documentation">Invalid bounty fee.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">PendingPayout (12)</td>
			<td data-label="Documentation">A bounty payout is pending. To cancel the bounty, you must unassign and slash the curator.</td>
		</tr>
		<tr>
			<th scope="row">Claims (24)</th>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">InvalidEthereumSignature (0)</td>
			<td data-label="Documentation">Invalid Ethereum signature.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">SignerHasNoClaim (1)</td>
			<td data-label="Documentation">Ethereum address has no claim.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">SenderHasNoClaim (2)</td>
			<td data-label="Documentation">Account ID sending tx has no claim.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">PotUnderflow (3)</td>
			<td data-label="Documentation">There's not enough in the pot to pay out some unvested amount. Generally implies a logic error.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">InvalidStatement (4)</td>
			<td data-label="Documentation">A needed statement was not included.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">VestedBalanceExists (5)</td>
			<td data-label="Documentation">The account already has a vested balance.</td>
		</tr>
		<tr>
			<th scope="row">Vesting (25)</th>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">NotVesting (0)</td>
			<td data-label="Documentation">The account given is not vesting.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">ExistingVestingSchedule (1)</td>
			<td data-label="Documentation">An existing vesting schedule already exists for this account that cannot be clobbered.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">AmountLow (2)</td>
			<td data-label="Documentation">Amount being transferred is too low to create a vesting schedule.</td>
		</tr>
		<tr>
			<th scope="row">Identity (28)</th>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">TooManySubAccounts (0)</td>
			<td data-label="Documentation">Too many subs-accounts.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">NotFound (1)</td>
			<td data-label="Documentation">Account isn't found.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">NotNamed (2)</td>
			<td data-label="Documentation">Account isn't named.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">EmptyIndex (3)</td>
			<td data-label="Documentation">Empty index.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">FeeChanged (4)</td>
			<td data-label="Documentation">Fee is changed.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">NoIdentity (5)</td>
			<td data-label="Documentation">No identity found.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">StickyJudgement (6)</td>
			<td data-label="Documentation">Sticky judgement.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">JudgementGiven (7)</td>
			<td data-label="Documentation">Judgement given.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">InvalidJudgement (8)</td>
			<td data-label="Documentation">Invalid judgement.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">InvalidIndex (9)</td>
			<td data-label="Documentation">The index is invalid.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">InvalidTarget (10)</td>
			<td data-label="Documentation">The target is invalid.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">TooManyFields (11)</td>
			<td data-label="Documentation">Too many additional fields.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">TooManyRegistrars (12)</td>
			<td data-label="Documentation">Maximum amount of registrars reached. Cannot add any more.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">AlreadyClaimed (13)</td>
			<td data-label="Documentation">Account ID is already named.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">NotSub (14)</td>
			<td data-label="Documentation">Sender is not a sub-account.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">NotOwned (15)</td>
			<td data-label="Documentation">Sub-account isn't owned by sender.</td>
		</tr>
		<tr>
			<th scope="row">Proxy (29)</th>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">TooMany (0)</td>
			<td data-label="Documentation">There are too many proxies registered or too many announcements pending.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">NotFound (1)</td>
			<td data-label="Documentation">Proxy registration not found.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">NotProxy (2)</td>
			<td data-label="Documentation">Sender is not a proxy of the account to be proxied.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">Unproxyable (3)</td>
			<td data-label="Documentation">A call which is incompatible with the proxy type's filter was attempted.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">Duplicate (4)</td>
			<td data-label="Documentation">Account is already a proxy.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">NoPermission (5)</td>
			<td data-label="Documentation">Call may not be made by proxy because it may escalate its privileges.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">Unannounced (6)</td>
			<td data-label="Documentation">Announcement, if made at all, was made too recently.</td>
		</tr>
		<tr>
			<th scope="row">Multisig (30)</th>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">MinimumThreshold (0)</td>
			<td data-label="Documentation">Threshold must be 2 or greater.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">AlreadyApproved (1)</td>
			<td data-label="Documentation">Call is already approved by this signatory.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">NoApprovalsNeeded (2)</td>
			<td data-label="Documentation">Call doesn't need any (more) approvals.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">TooFewSignatories (3)</td>
			<td data-label="Documentation">There are too few signatories in the list.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">TooManySignatories (4)</td>
			<td data-label="Documentation">There are too many signatories in the list.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">SignatoriesOutOfOrder (5)</td>
			<td data-label="Documentation">The signatories were provided out of order; they should be ordered.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">SenderInSignatories (6)</td>
			<td data-label="Documentation">The sender was contained in the other signatories; it shouldn't be.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">NotFound (7)</td>
			<td data-label="Documentation">Multisig operation not found when attempting to cancel.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">NotOwner (8)</td>
			<td data-label="Documentation">Only the account that originally created the multisig is able to cancel it.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">NoTimepoint (9)</td>
			<td data-label="Documentation">No timepoint was given, yet the multisig operation is already underway.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">WrongTimepoint (10)</td>
			<td data-label="Documentation">A different timepoint was given to the multisig operation that is underway.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">UnexpectedTimepoint (11)</td>
			<td data-label="Documentation">A timepoint was given, yet no multisig operation is underway.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">WeightTooLow (12)</td>
			<td data-label="Documentation">The maximum weight information provided was too low.</td>
		</tr>
		<tr>
			<th scope="row"></th>
			<td data-label="Error">AlreadyStored (13)</td>
			<td data-label="Documentation">The data to be stored is already stored.</td>
		</tr>
	</tbody>
</table>

<br></br>

<p align=right> Written by Masterdubs & Petar </p>

